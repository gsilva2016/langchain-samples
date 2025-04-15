# langchain-videochunk

This package contains the LangChain integration with VideoChunkLoader

## Installation

```bash
pip install -U .
```

## VideoChunkLoader

`VideoChunkLoader` class exposes a document loader for creating video chunks.

```python
from langchain_videochunk import VideoChunkLoader

loader = VideoChunkLoader(
    video_path="sample_video.mp4",
    chunking_mechanism="specific_chunks",
    specific_intervals="[ 
        {"start": 10, "duration": 10},
        {"start": 20, "duration": 8}
    ]
)

# or

loader = VideoChunkLoader(
    video_path="sample_video.mp4",
    chunking_mechanism="sliding_window",
    chunk_duration=10,
    chunk_overlap=2
)

docs = loader.lazy_load()
for doc in loader.lazy_load():
	print(f"Chunk metadata: {doc.metadata}")
	print(f"Chunk content: {doc.page_content}")
```
