---
title: Zdarzenia ETW w środowisku CLR
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: 5bb9b6a2-7b57-4aea-8809-32b28bc73e88
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 46ad58813da5b71b884ad55f796db3522b2f1920
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046613"
---
# <a name="etw-events-in-the-common-language-runtime"></a>Zdarzenia ETW w środowisku CLR
Środowisko uruchomieniowe języka wspólnego (CLR) zapewnia użyteczne informacje diagnostyczne śledzenia zdarzeń systemu Windows (ETW) za pomocą dużej różnorodności zdarzeń debugowania i profilowania. Zdarzenia ETW CLR wykorzystują system śledzenia funkcji ETW systemu Windows w celu rozszerzenia istniejącej obsługi profilowania i debugowania zapewnianej przez środowisko uruchomieniowe języka wspólnego.  
  
 Więcej informacji na temat funkcji ETW jest dostępnych w artykule [ulepszanie debugowania i dostrajania wydajności za pomocą funkcji ETW](https://go.microsoft.com/fwlink/?LinkID=161142) w witrynie MSDN. Informacje na temat Xperf można znaleźć w wpisie [Windows Performance Toolkit-Xperf](https://go.microsoft.com/fwlink/?LinkID=161144) w blogu NTDebugging.  
  
 W przypadku wszystkich zdarzeń opisanych w temacie zdarzenia jest wymagany .NET Framework 4 lub nowszy. System operacyjny Windows Vista jest minimalnym obsługiwanym klientem, a system Windows Server 2008 jest minimalnym obsługiwanym serwerem.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Kontrolowanie logowania w programie .NET Framework](controlling-logging.md)  
 Opisuje narzędzia i polecenia służące do przechwytywania i wyświetlania zdarzeń ETW.  
  
 [Dostawcy CLR ETW](clr-etw-providers.md)  
 Zawiera informacje o dostawcach środowiska uruchomieniowego i uwalniania oraz sposobie ich używania na potrzeby zbierania danych funkcji ETW.  
  
 [Słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md)  
 Zawiera opis słów kluczowych dla dostawców środowiska uruchomieniowego i rozmieszczonia, które umożliwiają filtrowanie zdarzeń według kategorii.  
  
 [Zdarzenia CLR ETW](clr-etw-events.md)  
 Zawiera szczegółowe informacje na temat zdarzeń ETW CLR, ich słów kluczowych, poziomów i danych zdarzeń.  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia ETW w programie .NET Framework](etw-events.md)
