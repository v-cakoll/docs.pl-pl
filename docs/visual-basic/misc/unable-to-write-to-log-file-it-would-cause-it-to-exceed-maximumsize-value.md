---
title: Nie można zapisać do pliku dziennika, ponieważ spowodowałoby przekroczenie wartości MaximumSize zapis do niego
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_FileExceedsMaximumSize
ms.assetid: 61747a9c-e460-424b-a365-73cdba9dd428
ms.openlocfilehash: 28a4b9286b13f8c7c72c4e98871846c2ca265aa9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619799"
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-cause-it-to-exceed-maximumsize-value"></a>Nie można zapisać do pliku dziennika, ponieważ spowodowałoby przekroczenie wartości MaximumSize zapis do niego
<xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Klasy nie można zapisać do pliku dziennika, ponieważ:  
  
- Rozmiar pliku dziennika (w bajtach) jest większa niż wartość <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> właściwości  
  
     — i —  
  
- Wartość <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> właściwość <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Archiwizowanie istniejące dzienniki i usuń je z komputera, aby umożliwić <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> obiekt, aby utworzyć nowe dzienniki.  
  
2. Zmień wartość właściwości <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> właściwości, aby umożliwić większe dzienniki.  
  
3. Ustaw <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> właściwości <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> do odrzucenia komunikaty bez ostrzeżenia, jeśli dziennik jest zbyt duży.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- [My.Application.Log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [My.Application.Info.DirectoryPath](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
