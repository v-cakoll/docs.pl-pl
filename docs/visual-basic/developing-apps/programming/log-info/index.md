---
title: Rejestrowanie informacji z aplikacji
ms.date: 07/20/2015
helpviewer_keywords:
- Log object
- My.Log object
- applications [Visual Basic], logging information from
- logging
- My.Application.Log object
- examples [Visual Basic], logging application information
ms.assetid: 8bf4f047-22d6-48d6-aec5-93b98ad5b8e8
ms.openlocfilehash: dace4bac3bf7529b8c50a492a092ad478f4d9e2d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353253"
---
# <a name="logging-information-from-the-application-visual-basic"></a>Rejestrowanie informacji z aplikacji (Visual Basic)

This section contains topics that cover how to log information from your application using the `My.Application.Log` or `My.Log` object, and how to extend the application's logging capabilities.  
  
 The `Log` object provides methods for writing information to the application's log listeners, and the `Log` object's advanced `TraceSource` property provides detailed configuration information. The `Log` object is configured by the application's configuration file.  
  
 The `My.Log` object is available only for ASP.NET applications. For client applications, use `My.Application.Log`. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Logging.Log>.  
  
## <a name="tasks"></a>Zadania  
  
|Do|Zobacz|  
|--------|---------|  
|Write event information to the application's logs.|[Instrukcje: zapisywanie komunikatów dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)|  
|Write exception information to the application's logs.|[Instrukcje: wyjątki dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)|  
|Write trace information to the application's logs when the application starts and shuts down.|[Instrukcje: rejestrowanie komunikatów podczas uruchamiania lub zamykania aplikacji](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|Configure `My.Application.Log` to write information to a text file.|[Instrukcje: zapisywanie informacji o zdarzeniach w pliku tekstowym](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)|  
|Configure `My.Application.Log` to write information to an event log.|[Instrukcje: zapisywanie w dzienniku zdarzeń aplikacji](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)|  
|Change where `My.Application.Log` writes information.|[Przewodnik: zmienianie lokalizacji, w której My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)|  
|Determine where `My.Application.Log` writes information.|[Przewodnik: ustalanie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)|  
|Create a custom log listener for `My.Application.Log`.|[Przewodnik: tworzenie odbiorców dzienników niestandardowych](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)|  
|Filter the output of the `My.Application.Log` logs.|[Przewodnik: filtrowanie danych wyjściowych My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Rozwiązywanie problemów: odbiorcy dzienników](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
