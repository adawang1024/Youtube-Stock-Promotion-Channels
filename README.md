# Youtube-Stock-Promotion-Channels


## Data Collection Methodology

Following the approach from _Influencers as Information Intermediaries_, we collected data on investment-related YouTube channels using the following steps:

### 1. **Channel Search:**  
   - We began by searching for channels using the keyword “investing,” which yielded an initial sample of 584 channels.

### 2. **Extraction of Top Words and Bigrams:**  
   - **Text Processing:** Channel titles and descriptions were cleaned and lowercased. Generic words and pronouns (e.g., "welcome," "channel," "I," "you") were excluded.
   - **TF-IDF Analysis:** We used `TfidfVectorizer` (scikit-learn) to rank term importance:
     - **Top 10 Words (Titles):** Unigrams from titles outstanding for the given title text
     - **Top 10 Words (Descriptions):** Unigrams from descriptions
     - **Top 10 Bigrams (Descriptions):** Bigrams (two-word phrases) from descriptions
   - **Selection Criteria:** Only included words/bigrams without numbers or punctuation, not in exclusion sets of generic words, and at least three characters long.
   - **Results:**

      **Top 10 Words (Titles):**  
      investing, invest, investment, investments, trading, podcast, stock, value, real, investors
      
      **Top 10 Words (Descriptions):**  
      investing, stock, investment, financial, market, invest, investors, trading, real, finance
      
      **Top 10 Bigrams (Descriptions):**  
      stock market, real estate, financial freedom, personal finance, long term, financial market, achieve financial, investing stock, cash flow, trading investing




### 3. Search Term Refinement

From the combined lists above, we identified the following unique search terms:

personal finance, value, financial freedom, stock market, investment, achieve financial, market, real estate, investing, investments, long term, stock, investors, financial market, financial, investing stock, podcast, trading investing, real, invest, finance, cash flow, trading. 


We decided to remove “podcast” and “real” as they were either too broad or more accurately captured in terms like “real estate.”

#### Comparison to the Paper

The original paper included some additional, more generic terms not present in our initial list, such as: channel, stocks, videos, money, make, personal, learn, advice, help, journey, share.

- We **added** “stocks” (since searching for “stocks” can yield different results from “stock” due to the API’s 500-result cap for eahc keyword), as well as “money” and “share” for greater coverage.
- We **did not include** other terms that were deemed too general and less relevant to investing content.

### Final 24 Search Terms

Our final set of 24 search terms is:

personal finance, value, financial freedom, stock market, investment, achieve financial, market, real estate, investing, investments, long term, stock, investors, financial market, financial, investing stock, trading investing, invest, finance, cash flow, trading, stocks(added), money(added), share(added). 


### 4. Channel Collection
We then used these terms as search keywords for videos (YouTube searches for the term in all metadata fields, including title and description), which resulted in 9,642 unique channels. For each channel, we used the YouTube Channels API to retrieve channel information such as description, video count, and subscriber count. 

### 5. Filtering

To ensure data quality and relevance, we applied the following filters to the channels:

- **Language:** Only channels with English content were included.
- **Audience Size:** Channels were required to have more than 10,000 subscribers, excluding micro-influencers.
- **Activity:** Channels needed to have published at least 10 videos.
 


