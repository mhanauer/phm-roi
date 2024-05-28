import streamlit as st 

import pandas as pd 

from pyprojroot import here

import os
  

def main(): 

    # Load the dataset 
    path_data = here("./data")
    os.chdir(path_data)

    data = pd.read_csv('data_analyses_phm_roi_demo.csv') 

  

    # Streamlit application 

    st.title('PHM ROI Example') 

  

    st.markdown(""" 

    ### Definitions: 

    - **3-Month ROI**: We are looking at the average 3 months before (pre-intervention) the intervention start and then the average for 3 months after 3 months in the intervention (post-intervention). 

    - **Difference Scores**: Post-intervention - Pre-intervention 

    - **Predicted Difference Score**: Difference predicted if the member never had the intervention 

    - **Change cost scores**: Difference score - Predicted difference score - Program costs
    
    - **ROI**: (Difference score - Predicted difference score) / Program costs 

    """) 

  

    # Filter for intervention group with limited options 

    intervention_group = st.selectbox( 

        'Select Intervention Group', 

        options=['both', 'omada', 'web_md'] 

    ) 

  

    # Filter the data based on the selected intervention group 

    filtered_data = data[data['intervention_group'] == intervention_group] 

  

    # Calculate mean and total ROI 

    mean_costs_changes = filtered_data['change_costs'].mean() 

    total_costs_changes = filtered_data['roi_costs'].sum() 
    
    mean_roi_costs = filtered_data['roi_costs'].mean() 

    mean_roi_er_visits = filtered_data['roi_er_visits'].mean() 

    total_roi_er_visits = filtered_data['roi_er_visits'].sum() 

  

    # Display the mean and total ROI 

    st.subheader(f'3-Month Mean and Total ROI for {intervention_group.capitalize()} Group') 

    st.write(f"3-Month Mean  Changes (Costs): ${mean_costs_changes:,.2f}") 

    st.write(f"3-Month Total  Changes (Costs): ${total_costs_changes:,.2f}")
    
    st.write(f"3-Month ROI Costs: {mean_roi_costs:.2f}")

    st.write(f"3-Month Mean Changes (ER Visits): {mean_roi_er_visits:.2f}") 

    st.write(f"3-Month Total Changes (ER Visits): {total_roi_er_visits:.2f}") 

  

    # Display the filtered table 

    st.subheader('Data') 

    st.dataframe(filtered_data) 

  

# Run Streamlit application 

if __name__ == '__main__': 

    main() 

 