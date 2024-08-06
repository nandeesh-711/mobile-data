# mobile-data
import pandas as pd 
import numpy as np 
import matplotlib.pyplot as plt 
  

DATASET_FILENAME = 'june24_publish.csv'
CONST_OPERATOR = 'JIO'
CONST_STATE = 'Delhi'
CONST_TECHNOLOGY = '4G'
final_download_speeds = [] 
final_upload_speeds = [] 
final_states = [] 
final_operators = [] 
df = pd.read_csv('june24_publish.csv') 

df.columns = ['Service Provider', 'Technology', 'Test Type', 
                   'Data Speed', 'Signal Strength', 'State'] 
                   states = df['State'].unique() 
print('STATES Found: ', states) 
  

operators = df['Service Provider'].unique() 
print('OPERATORS Found: ', operators) 

filtered = df[(df['Service Provider'] == CONST_OPERATOR)  
               & (df['Technology'] == CONST_TECHNOLOGY)] 
  

for state in states: 
  
   
    base = filtered[filtered['State'] == state] 
  
   
    down = base[base['Test Type'] == 'download'] 
  

    up = base[base['Test Type'] == 'upload'] 
  
   
    avg_down = down['Data Speed'].mean() 
  
   
    avg_up = up['Data Speed'].mean() 
  

    if (pd.isnull(avg_down) or pd.isnull(avg_up)): 
        down, up = 0, 0
      
    else: 
        final_states.append(state) 
        final_download_speeds.append(avg_down) 
        final_upload_speeds.append(avg_up) 
  

        print(str(state) + ' -- Avg. Download: ' +
                          str('%.2f' % avg_down) + 
         '  Avg. Upload: ' + str('%.2f' % avg_up)) 
         
fig, ax = plt.subplots() 
bar_width = 0.25
opacity = 0.8
index = np.arange(len(final_states)) 
bar_download = plt.bar(index, final_download_speeds, 
                       bar_width, alpha=opacity, 
                       color='b', label='Download') 
  
bar_upload = plt.bar(index + bar_width, final_upload_speeds,  
                        bar_width, alpha=opacity, color='g', 
                                             label='Upload') 
   

plt.title('Avg. Download/Upload speed for '
                     + str(CONST_OPERATOR)) 
plt.xlabel('States') 
plt.ylabel('Average Speeds in Kbps') 
plt.xticks(index + bar_width, final_states, rotation=90) 
plt.legend() 
plt.tight_layout() 
plt.show() 
