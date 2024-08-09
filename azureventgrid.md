Azure Event Grid
|
|-- Overview
|   |-- Event Grid Topics       # Topics for publishing events
|   |-- Event Grid Subscriptions # Subscriptions for handling events
|   |-- Event Grid Domains       # Custom domains for events
|   |-- Event Grid System Topics # Built-in topics for Azure services
|
|-- Commands
|   |-- Topics
|   |   |-- Create Topic         # Create a new Event Grid topic
|   |   |   |-- Use `az eventgrid topic create --name <topic-name> --resource-group <resource-group> --location <location>`
|   |   |-- List Topics          # List all Event Grid topics
|   |   |   |-- Use `az eventgrid topic list --resource-group <resource-group>`
|   |   |-- Show Topic Details   # Show details of a specific topic
|   |   |   |-- Use `az eventgrid topic show --name <topic-name> --resource-group <resource-group>`
|   |   |-- Delete Topic         # Delete an Event Grid topic
|   |       |-- Use `az eventgrid topic delete --name <topic-name> --resource-group <resource-group>`
|   |
|   |-- Subscriptions
|   |   |-- Create Subscription   # Create a new Event Grid subscription
|   |   |   |-- Use `az eventgrid event-subscription create --name <subscription-name> --source-resource-id <source-id> --endpoint <endpoint-url>`
|   |   |-- List Subscriptions    # List all Event Grid subscriptions
|   |   |   |-- Use `az eventgrid event-subscription list --source-resource-id <source-id>`
|   |   |-- Show Subscription     # Show details of a specific subscription
|   |   |   |-- Use `az eventgrid event-subscription show --name <subscription-name> --source-resource-id <source-id>`
|   |   |-- Delete Subscription   # Delete an Event Grid subscription
|   |       |-- Use `az eventgrid event-subscription delete --name <subscription-name> --source-resource-id <source-id>`
|   |
|   |-- Domains
|   |   |-- Create Domain         # Create a new Event Grid domain
|   |   |   |-- Use `az eventgrid domain create --name <domain-name> --resource-group <resource-group> --location <location>`
|   |   |-- List Domains          # List all Event Grid domains
|   |   |   |-- Use `az eventgrid domain list --resource-group <resource-group>`
|   |   |-- Show Domain Details   # Show details of a specific domain
|   |   |   |-- Use `az eventgrid domain show --name <domain-name> --resource-group <resource-group>`
|   |   |-- Delete Domain         # Delete an Event Grid domain
|   |       |-- Use `az eventgrid domain delete --name <domain-name> --resource-group <resource-group>`
|   |
|   |-- System Topics
|       |-- List System Topics    # List all system topics
|       |   |-- Use `az eventgrid system-topic list --resource-group <resource-group>`
|       |-- Show System Topic Details # Show details of a specific system topic
|           |-- Use `az eventgrid system-topic show --name <system-topic-name> --resource-group <resource-group>`

Azure Queue Storage
|
|-- Overview
|   |-- Queues                    # Queues for storing messages
|
|-- Commands
|   |-- Queues
|   |   |-- Create Queue         # Create a new queue
|   |   |   |-- Use `az storage queue create --name <queue-name> --account-name <account-name>`
|   |   |-- List Queues           # List all queues
|   |   |   |-- Use `az storage queue list --account-name <account-name>`
|   |   |-- Show Queue Properties # Show properties of a specific queue
|   |   |   |-- Use `az storage queue show --name <queue-name> --account-name <account-name>`
|   |   |-- Delete Queue         # Delete a queue
|   |       |-- Use `az storage queue delete --name <queue-name> --account-name <account-name>`
|   |
|   |-- Messages
|   |   |-- Send Message          # Send a message to a queue
|   |   |   |-- Use `az storage message put --queue-name <queue-name> --account-name <account-name> --text <message-text>`
|   |   |-- List Messages         # List messages in a queue
|   |   |   |-- Use `az storage message list --queue-name <queue-name> --account-name <account-name>`
|   |   |-- Peek Messages         # Peek at messages without removing them
|   |   |   |-- Use `az storage message peek --queue-name <queue-name> --account-name <account-name>`
|   |   |-- Delete Message        # Delete a message from a queue
|   |       |-- Use `az storage message delete --queue-name <queue-name> --account-name <account-name> --message-id <message-id> --pop-receipt <pop-receipt>`
|
|-- Samples
|   |-- Event Grid
|   |   |-- Create a Topic
|   |   |   |-- Sample: `az eventgrid topic create --name myTopic --resource-group myResourceGroup --location westus`
|   |   |-- Create a Subscription
|   |   |   |-- Sample: `az eventgrid event-subscription create --name mySubscription --source-resource-id /subscriptions/<subscription-id>/resourceGroups/myResourceGroup/providers/Microsoft.EventGrid/topics/myTopic --endpoint https://myendpoint.com/api/events`
|   |   |-- Send Event to Topic
|   |       |-- Sample: `az eventgrid event-publisher send --topic-name myTopic --resource-group myResourceGroup --events '[{"id":"1","subject":"test","data":{"key":"value"},"eventType":"myEvent","eventTime":"2024-08-09T00:00:00Z"}]'`
|   |
|   |-- Queue Storage
|       |-- Create a Queue
|       |   |-- Sample: `az storage queue create --name myQueue --account-name myStorageAccount`
|       |-- Send a Message
|       |   |-- Sample: `az storage message put --queue-name myQueue --account-name myStorageAccount --text "Hello, World!"`
|       |-- Peek at Messages
|           |-- Sample: `az storage message peek --queue-name myQueue --account-name myStorageAccount`
