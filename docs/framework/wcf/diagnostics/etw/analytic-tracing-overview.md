---
title: Omówienie śledzenia analitycznego
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF], overview
ms.assetid: ae55e9cc-0809-442f-921f-d644290ebf15
ms.openlocfilehash: 9918f07d9c26c1779a1eedfbc423c31e61659334
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401184"
---
# <a name="analytic-tracing-overview"></a>Omówienie śledzenia analitycznego
Śledzenie danych analitycznych w [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] o wysokiej wydajności i funkcję śledzenia niski poziom szczegółowości, ustaw na podstawie śledzenie zdarzeń dla Windows (ETW). ETW działa na poziomie jądra można znacznie zmniejszyć koszty operacji śledzenia. Efektywnie je buforuje zdarzenia trybu jądra i użytkownika i umożliwia dynamiczne Włączanie rejestrowania bez konieczności ponownego uruchomienia usługi. Dane śledzenia są dostępne, w przypadku dzienników po nim został wyemitowany i odebranych.  
  
 Aby uzyskać więcej informacji na temat funkcji ETW, zobacz [poprawić debugowania i dostrajania wydajności za pomocą funkcji ETW](https://go.microsoft.com/fwlink/?LinkId=164781).  
  
 Oprócz używania dzienników zdarzeń systemu Windows, zabezpieczeń i aplikacji do analizowania aplikacji, [!INCLUDE[wv](../../../../../includes/wv-md.md)] i [!INCLUDE[lserver](../../../../../includes/lserver-md.md)] wprowadzono dodatkowe dzienniki w obszarze Dzienniki aplikacji i usług węzła najwyższego poziomu. Te nowe dzienniki ma na celu przechowywania zdarzeń dla określonej aplikacji lub określonego składnika, a nie zdarzenia globalne, które mają wpływ systemowe (takie jak typ zdarzenia, które może zarejestrować w dzienniku zdarzeń zabezpieczeń). [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] łączy i koreluje rejestrowanie zdarzeń śledzenia WCF, dzienników komunikatów WCF, i [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] śledzenia rekordów Dzienniki aplikacji i usług.  
  
## <a name="concepts-and-capabilities"></a>Pojęcia i możliwości  
 Następujące pojęcia i możliwości dotyczą analityczne śledzenia WCF.  
  
### <a name="enabling-wcf-diagnostics-settings"></a>Włączanie ustawień diagnostycznych programu WCF  
 Diagnostyka usługi WCF jest włączona w ramach \<system.serviceModel >\<Diagnostyka > Sekcja konfiguracji.  
  
```xml  
<system.serviceModel>  
  <diagnostics>  
```  
  
 Ustawienia diagnostyczne usługi WCF hostowanej w sieci Web usług IIS aplikacji wirtualnej są włączone w jej "pliku Web.config. Innym rozwiązaniem jest, aby utworzyć plik Web.config w podkatalogu w aplikacji.  Ten wybór stosuje ustawienia do wszystkich usług w podkatalogu.  Aby upewnić się, że ustawienia diagnostyczne są inicjowane spójne dla wszystkich usług w aplikacji, ustawienia należy w pliku Web.config w katalogu aplikacji, a nie w poszczególnych katalogów podrzędne w ramach aplikacji.  
  
### <a name="channels"></a>Kanały  
 ETW umożliwia składniki oprogramowania do bezpośredniego śledzenie zdarzeń do określonej grupy odbiorców przy użyciu kanałów. Na przykład możesz wysłać zdarzenia dla administratorów systemów do jednego kanału i zdarzenia tego opieki deweloperom aplikacji o na inną drogą. Kanały są o nazwie i zarejestrowane w usłudze Windows, dzięki czemu użytkownicy mogą wyświetlać zdarzenia kanału, za pomocą Podglądu zdarzeń.  
  
 Funkcja śledzenia danych analitycznych programu WCF w [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] zapisuje do aplikacji firmy Microsoft-Windows-aplikacji-Server kanału. Ten kanał jest specjalnie przeznaczona dla użytkowników, którzy chcą do monitorowania prawidłowości usługi WCF w środowisku produkcyjnym. Definiuje on mały zestaw zdarzeń, które mogą być używane w wielu monitorowania kondycji i rozwiązywanie problemów ze scenariuszami.  
  
 Aby włączyć manifest Event Tracing for Windows, dzięki czemu komunikaty są poprawnie dekodowane w dzienniku zdarzeń, należy użyć narzędzia ServiceModelReg w wierszu polecenia w następujący sposób:  
  
 `ServiceModelReg.exe -i -c:etw`  
  
### <a name="dynamic-configuration"></a>Dynamiczna konfiguracja  
 Infrastruktury ETW umożliwia śledzenie, aby być włączona i skonfigurowana, dynamicznie przy użyciu standardowych narzędzi Windows. Aby uzyskać więcej informacji, zobacz [dynamiczne Włączanie analizy śledzenia](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md).  
  
### <a name="message-flow-tracing"></a>Śledzenia przepływu komunikatów  
 Aby uzyskać więcej informacji o sposobie włączania śledzenia przepływu komunikatów, zobacz [Konfigurowanie śledzenia przepływu komunikatów](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md).  
  
### <a name="keywords"></a>Słowa kluczowe  
 Słowa kluczowe są używane do filtrowania komunikatów śledzenia i określić które składnik [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] emitowane zdarzenia. Aby uzyskać więcej informacji, zobacz [dynamiczne Włączanie analizy śledzenia](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md).
