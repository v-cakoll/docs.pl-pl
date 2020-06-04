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
ms.openlocfilehash: 43738b2d654435532a98654cbc40af134d43f02c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410026"
---
# <a name="logging-information-from-the-application-visual-basic"></a>Rejestrowanie informacji z aplikacji (Visual Basic)

Ta sekcja zawiera tematy, które opisują, jak rejestrować informacje z aplikacji przy `My.Application.Log` użyciu `My.Log` obiektu lub i jak zwiększyć możliwości rejestrowania aplikacji.  
  
 `Log`Obiekt zawiera metody zapisywania informacji w detektorach dzienników aplikacji, a `Log` Właściwość zaawansowana obiektu `TraceSource` zawiera szczegółowe informacje o konfiguracji. `Log`Obiekt jest konfigurowany przez plik konfiguracyjny aplikacji.  
  
 `My.Log`Obiekt jest dostępny tylko dla aplikacji ASP.NET. W przypadku aplikacji klienckich Użyj programu `My.Application.Log` . Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Logging.Log>.  
  
## <a name="tasks"></a>Zadania  
  
|Do|Zobacz|  
|--------|---------|  
|Zapisz informacje o zdarzeniu w dziennikach aplikacji.|[Instrukcje: zapisywanie komunikatów dziennika](how-to-write-log-messages.md)|  
|Zapisz informacje o wyjątkach w dziennikach aplikacji.|[Instrukcje: rejestrowanie wyjątków](how-to-log-exceptions.md)|  
|Zapisuj informacje o śledzeniu do dzienników aplikacji podczas uruchamiania i zamykania aplikacji.|[Instrukcje: rejestrowanie komunikatów podczas uruchamiania lub zamykania aplikacji](how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|Skonfiguruj `My.Application.Log` , aby zapisywać informacje w pliku tekstowym.|[Instrukcje: zapisywanie informacji o zdarzeniach w pliku tekstowym](how-to-write-event-information-to-a-text-file.md)|  
|Skonfiguruj `My.Application.Log` , aby zapisywać informacje w dzienniku zdarzeń.|[Instrukcje: zapisywanie w dzienniku zdarzeń aplikacji](how-to-write-to-an-application-event-log.md)|  
|Zmień miejsce `My.Application.Log` zapisu informacji.|[Przewodnik: zmienianie lokalizacji, w której element My.Application.Log zapisuje informacje](walkthrough-changing-where-my-application-log-writes-information.md)|  
|Określ, gdzie są `My.Application.Log` zapisywane informacje.|[Przewodnik: ustalanie lokalizacji, w której element My.Application.Log zapisuje informacje](walkthrough-determining-where-my-application-log-writes-information.md)|  
|Utwórz odbiornik dziennika niestandardowego dla programu `My.Application.Log` .|[Przewodnik: tworzenie odbiorców dzienników niestandardowych](walkthrough-creating-custom-log-listeners.md)|  
|Filtrowanie danych wyjściowych `My.Application.Log` dzienników.|[Przewodnik: filtrowanie danych wyjściowych elementu My.Application.Log](walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Praca z dziennikami aplikacji](working-with-application-logs.md)
- [Rozwiązywanie problemów: odbiorcy dzienników](troubleshooting-log-listeners.md)
