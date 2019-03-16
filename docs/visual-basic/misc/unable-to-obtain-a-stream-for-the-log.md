---
title: Nie można uzyskać strumień dziennika
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
ms.openlocfilehash: 45b7a16608bea4879e84fa7004097a8c38312284
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "58031710"
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a>Nie można uzyskać strumień dziennika
Nie można uzyskać strumienia dziennika. Potencjalne nazwy plików na podstawie \<name > jest już w użyciu.  
  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Klasy nie można utworzyć nowy plik dziennika, ponieważ wszystkie potencjalne nazwy plików dziennika na podstawie \<name > jest już w użyciu.  
  
 Masz zbyt wiele plików dziennika może wskazywać architektury problem z aplikacją. Zobacz dokumentację <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> klasy, aby uzyskać więcej informacji.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Ustaw <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> właściwości <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> lub <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> obejmujący sygnatura daty w nazwie pliku dziennika.  
  
2.  Archiwizowanie istniejące dzienniki i usuń je z komputera, aby umożliwić <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> obiekt, aby utworzyć nowe dzienniki.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>
- [My.Application.Log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [My.Application.Info.DirectoryPath](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
