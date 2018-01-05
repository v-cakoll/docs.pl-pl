---
title: "Nie można zapisać do pliku dziennika, ponieważ zapisanie może spowodować przekroczenie wartości MaximumSize"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrApplicationLog_FileExceedsMaximumSize
ms.assetid: 61747a9c-e460-424b-a365-73cdba9dd428
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4004dca2a3b9f13583cfdfe43f89bc4bff5dd6d6
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-cause-it-to-exceed-maximumsize-value"></a>Nie można zapisać do pliku dziennika, ponieważ zapisanie może spowodować przekroczenie wartości MaximumSize
<xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Klasy nie można zapisać do pliku dziennika, ponieważ:  
  
-   Rozmiar pliku dziennika (w bajtach) jest większa niż wartość <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> właściwości  
  
     - i -  
  
-   Wartość <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> właściwość <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Archiwizowanie istniejące dzienniki i usuń je z komputera, aby umożliwić <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> obiekt, aby utworzyć nowe dzienniki.  
  
2.  Zmień wartość <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> właściwości, aby umożliwić większe dzienniki.  
  
3.  Ustaw <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> właściwości <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> odrzucić wiadomości bez ostrzeżenia, jeśli dziennik jest zbyt duży.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
 [My.Application.Log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)  
 [My.Application.Info.DirectoryPath](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
