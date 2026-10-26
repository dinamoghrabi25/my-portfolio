# XYZ Real Estate Assistant

> An AI-powered real estate assistant built with n8n that interacts with potential property buyers through Telegram, collects their preferences, and connects conversational AI with a workflow that includes Google Sheets.

---

## 🎯 Problem

### The Context

Real estate agencies often need to communicate with potential buyers, understand their requirements, and collect information before recommending suitable properties.

### The Problem

Collecting buyer information through conversations can require repetitive questions and manual follow-up. Important details such as budget, purchasing timeline, and contact information need to be gathered in an organized way.

### Why It Matters

A structured conversational assistant can make initial communication more consistent, simplify information collection, and help organize potential customer inquiries for follow-up.

---

## 💡 Solution

I developed an AI-powered real estate assistant using n8n and Telegram. The workflow connects incoming Telegram messages to an AI Agent, which conducts a conversation with the user and sends responses back through Telegram.

The workflow also includes Simple Memory, an OpenRouter Chat Model, and a Google Sheets integration configured to append rows.

What does the system do?

1. Receives user messages through a Telegram Trigger.
2. Processes the conversation through an AI Agent connected to a chat model and memory.
3. Asks questions to understand the potential buyer's requirements, including budget and purchasing timeline.
4. Sends conversational responses through Telegram and includes a Google Sheets node configured to append rows.

---

## 👤 Users

**Primary Users:**

Potential property buyers and real estate professionals who need a structured way to collect and manage initial property inquiries.

**User Need:**

To communicate with an assistant, provide property-buying preferences, and share relevant information through a guided conversation.

---

## 🧠 How I Designed the Solution

I designed the workflow around a conversational interface so that users could provide information naturally through Telegram rather than completing a conventional form.

The workflow separates the main responsibilities into connected components:

- Telegram handles incoming messages and outgoing responses.
- The AI Agent manages the conversational interaction.
- The OpenRouter Chat Model provides the language-model connection.
- Simple Memory provides a memory component for the AI Agent.
- Google Sheets is included as a data-handling integration.

This modular structure makes the workflow easier to understand and extend as the project develops.

---

## ⚙️ How It Works

```text
User sends a message on Telegram
              ↓
       Telegram Trigger
              ↓
           AI Agent
          ↙    ↓    ↘
   Chat Model  Memory  Google Sheets
              ↓
     Generate a response
              ↓
    Send a text message
              ↓
      User receives reply
```

*Note: This diagram represents the visible workflow structure. The exact execution order and the successful operation of every integration should be verified through n8n execution logs.*

---

## 🤖 Role of AI

The AI component is intended to support natural-language interaction with potential property buyers.

- Conducts a conversational exchange with the user.
- Asks follow-up questions to collect relevant purchasing preferences.
- Generates responses based on the conversation and configured model.

### What AI Should NOT Do

- Invent property listings, prices, or availability.
- Treat unverified customer information as confirmed.
- Make financial or legal commitments on behalf of a real estate agency.
- Claim that information has been saved unless the relevant operation succeeds.

---

## 🔄 Automation

The n8n workflow connects several steps that would otherwise require separate manual actions.

- Receiving Telegram messages through a trigger.
- Passing conversation input to an AI Agent.
- Sending generated text responses back through Telegram.
- Including a Google Sheets node configured to append rows.

The exact data saved in Google Sheets and the successful execution of the complete automation remain to be verified.

---

## 🗂️ Data

### Input

The workflow receives messages from Telegram users. The demonstrated conversation includes:

- Purchasing timeline.
- Property budget.
- Buyer's name.
- A question requesting an email address.

### Output

The demonstrated interaction includes conversational replies in Arabic. The visible workflow also contains a Telegram response node and a Google Sheets append-row node.

The exact spreadsheet columns, stored fields, and persistence of conversation history should be confirmed from the node configurations and execution data.

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| n8n | Workflow orchestration and automation |
| Telegram Bot | User interaction and message delivery |
| AI Agent | Conversational workflow component |
| OpenRouter Chat Model | Language-model integration |
| Simple Memory | Memory component connected to the AI Agent |
| Google Sheets | Spreadsheet integration configured to append rows |

---

## 🔑 Key Design Decisions

### Decision 1: Telegram as the User Interface

**Decision:** Use Telegram as the conversational interface.

**Why:** It allows users to interact through familiar text messages without requiring a separate web application.

### Decision 2: An AI Agent for Conversational Interaction

**Decision:** Connect the incoming messages to an AI Agent with a chat-model connection.

**Why:** This structure supports natural-language responses and follow-up questions rather than relying exclusively on fixed form fields.

### Decision 3: Include Memory and a Spreadsheet Integration

**Decision:** Include Simple Memory and Google Sheets in the workflow.

**Why:** Memory provides a component for conversational context, while the spreadsheet integration can support structured recordkeeping when configured and tested successfully.

---

## 🧪 Testing

### Test 1: Telegram Conversation

**Input:**

A user interacts with the Telegram bot and provides a budget of `100000`.

**Expected Result:**

The assistant should interpret the budget and continue the conversation appropriately.

**Actual Result:**

The visible Telegram conversation shows the assistant responding that the budget is USD 100,000 and falls below USD 200,000. The assistant then asks for the user's first and last name.

**Status:** Observed in the provided screenshot.

### Test 2: Requesting Contact Information

**Input:**

The user provides the name `دينا المغربي`.

**Expected Result:**

The assistant acknowledges the name and proceeds to request the user's email address.

**Actual Result:**

The screenshot shows the assistant acknowledging the name and asking whether the user has an email address. The subsequent completion of this step is not shown.

**Status:** Partially verified.

### Test 3: Google Sheets Integration

**Input:**

A conversation containing buyer information.

**Expected Result:**

The configured Google Sheets node appends the intended information to a spreadsheet row.

**Actual Result:**

The provided workflow screenshot shows an `Append row in sheet` node connected to the AI Agent's Tool port. No execution result or spreadsheet record was provided to confirm successful data insertion.

**Status:** Pending verification.

---

## 📸 Evidence

### Final Result: Telegram Conversation

Add the screenshot showing the assistant's Arabic conversation with the user, including the budget interpretation and follow-up questions.

Suggested filename:

`screenshots/telegram-conversation.png`

### Workflow Architecture

Add the screenshot showing the n8n workflow and its connected nodes.

Suggested filename:

`screenshots/n8n-workflow.png`

### Optional Additional Evidence

Once available, include:

- A successful n8n execution showing the workflow in operation.
- A screenshot of the corresponding Google Sheets row, with personal information removed.
- A short screen recording demonstrating the conversation from beginning to end.

---

## ⚠️ Challenges & Failures

The current evidence does not establish any specific technical failure or its resolution.

Potential areas to validate during development include:

- Maintaining relevant context throughout a multi-message conversation.
- Ensuring that budget values are interpreted correctly.
- Handling missing or invalid contact information.
- Confirming that Google Sheets receives the intended fields.
- Preventing duplicate or incomplete records.

These are validation areas, not confirmed failures.

---

## 📚 What I Learned

### Technical Lesson

The workflow demonstrates how n8n can connect messaging platforms, AI components, memory, and spreadsheet integrations in a single automation design.

### Problem-Solving Lesson

A conversational interface can gather information incrementally, allowing users to provide details in natural language.

### AI Lesson

An AI Agent needs a well-defined task, appropriate context, and reliable integrations. Each connected component must be tested independently and as part of the complete workflow.

---

## 🔮 Future Improvements

If I continue developing this project, I would:

- Verify the complete conversation flow, including email collection.
- Test memory behavior across multiple messages.
- Validate the Google Sheets integration and define the exact fields to save.
- Add input validation and handling for incomplete responses.
- Test error handling and duplicate-record prevention.
- Improve the assistant's property-related responses using verified property data.
- Document a complete end-to-end execution with test data.

---

## 🔗 Project Links

**Live Demo:** Not publicly available.

**Workflow:** Available in the n8n workspace; a shareable workflow link has not been provided.

**Repository:** Not provided.

---

## 👩‍💻 Author

**Dina Almughrabi**

AI Engineering & Intelligent Automation
