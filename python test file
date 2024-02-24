# Import necessary libraries
import streamlit as st
import yfinance as yf
import pandas as pd
import matplotlib.pyplot as plt

# Streamlit setup
st.title('Stock Market Analysis')

# Sidebar for user input
st.sidebar.header('Enter Stock Ticker')
ticker = st.sidebar.text_input("Enter a valid stock ticker (e.g., AAPL for Apple):")

# Function to retrieve stock data
def get_stock_data(ticker, start_date, end_date):
    stock = yf.Ticker(ticker)
    data = stock.history(start=start_date, end=end_date)
    return data

# Main content
if ticker:
    st.subheader('Stock Data')
    
    # Retrieve data
    try:
        stock_data = get_stock_data(ticker, '2020-01-01', '2024-01-01')
        
        # Display data
        st.write(stock_data)
        
        # Plot closing price
        st.subheader('Closing Price')
        plt.figure(figsize=(10, 6))
        plt.plot(stock_data['Close'])
        plt.xlabel('Date')
        plt.ylabel('Closing Price ($)')
        plt.title(f'{ticker} Closing Price')
        st.pyplot()

        # Simple analysis
        st.subheader('Simple Analysis')
        st.write(f"Maximum Closing Price: {stock_data['Close'].max()}")
        st.write(f"Minimum Closing Price: {stock_data['Close'].min()}")
        st.write(f"Mean Closing Price: {stock_data['Close'].mean()}")
        
    except Exception as e:
        st.error(f"Error: {e}")
