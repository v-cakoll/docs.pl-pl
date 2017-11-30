---
title: "Nie można uzyskać strumienia dla dziennika"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dd3051b2331502c9f4f3430bbf88731b307d1b1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a>Nie można uzyskać strumienia dla dziennika
Nie można uzyskać strumienia dla dziennika. Potencjalne nazwy plików oparte na \<name > są już używane.  
  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Klasy nie można utworzyć nowy plik dziennika, ponieważ wszystkie potencjalne nazwy plików dziennika na podstawie \<name > są już używane.  
  
 O zbyt wiele plików dziennika może wskazywać architektury problem z aplikacją. Zajrzyj do dokumentacji <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> klasy, aby uzyskać więcej informacji.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Ustaw <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> właściwości <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> lub <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> uwzględnienie sygnaturę daty w polu Nazwa pliku dziennika.  
  
2.  Archiwizowanie istniejące dzienniki i usuń je z komputera, aby umożliwić <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> obiekt, aby utworzyć nowe dzienniki.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>  
 [My.Application.log — obiekt](../../visual-basic/language-reference/objects/my-application-log-object.md)  
 [My.log — obiekt](../../visual-basic/language-reference/objects/my-log-object.md)
