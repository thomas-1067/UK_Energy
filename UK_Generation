import streamlit as st
import requests
import pandas as pd
import plotly.express as px

st.set_page_config(page_title="UK Electricity Mix", layout="wide")

st.title("🔌 Live UK Electricity Generation Mix")

# Fetch data from Carbon Intensity API
url = "https://api.carbonintensity.org.uk/generation"
r = requests.get(url)
data = r.json()

# Check the structure of the response
generation = data["data"]["generationmix"]
df = pd.DataFrame(generation).sort_values("perc", ascending=False)

# Show table
st.subheader("Current Generation Mix (% of total)")
st.dataframe(df, use_container_width=True)

# Show pie chart
fig = px.pie(df, values="perc", names="fuel", title="Electricity Mix")
st.plotly_chart(fig, use_container_width=True)
