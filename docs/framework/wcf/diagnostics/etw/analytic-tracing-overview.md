---
title: Omówienie śledzenia analitycznego
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF], overview
ms.assetid: ae55e9cc-0809-442f-921f-d644290ebf15
ms.openlocfilehash: f1a24e34375e98d4bfb48c1e2fd84290e08f6eea
ms.sourcegitcommit: 8c99457955fc31785b36b3330c4ab6ce7984a7ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/29/2019
ms.locfileid: "75544752"
---
# <a name="analytic-tracing-overview"></a>Omówienie śledzenia analitycznego
Śledzenie analityczne w [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] to funkcja śledzenia o wysokiej wydajności i niskim poziomie szczegółowości dla systemu Windows (ETW). Funkcja ETW działa na poziomie jądra, aby znacznie zmniejszyć obciążenie operacji śledzenia. Efektywnie buforuje zdarzenia użytkownika i trybu jądra oraz umożliwia dynamiczne Włączanie rejestrowania bez konieczności ponownego uruchamiania usługi. Dane śledzenia są dostępne w dziennikach zdarzeń po ich emisji i odebraniu.  
  
 Aby uzyskać więcej informacji na temat funkcji ETW, zobacz [ulepszanie debugowania i dostrajania wydajności za pomocą funkcji ETW](https://go.microsoft.com/fwlink/?LinkId=164781).  
  
 Oprócz korzystania z dzienników zdarzeń systemu Windows, zabezpieczeń i aplikacji do analizowania aplikacji, Windows Vista i Windows Server 2008 wprowadzono dodatkowe dzienniki w węźle aplikacje i usługi Dzienniki najwyższego poziomu. Te nowe dzienniki mają na celu przechowywanie zdarzeń dla konkretnej aplikacji lub określonego składnika zamiast zdarzeń globalnych, które mają wpływ na cały system (na przykład typ zdarzeń, które mogą być rejestrowane w dzienniku zdarzeń zabezpieczeń). [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] łączy i skorelowanie rejestrowania zdarzeń śledzenia WCF, dzienników komunikatów WCF i [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] śledzenia rekordów w dziennikach aplikacji i usług.  
  
## <a name="concepts-and-capabilities"></a>Koncepcje i możliwości  
 Poniższe koncepcje i możliwości dotyczą śledzenia analitycznego WCF.  
  
### <a name="enabling-wcf-diagnostics-settings"></a>Włączanie ustawień diagnostycznych WCF  
 Diagnostyka WCF jest włączona w sekcji \<system. serviceModel >\<Diagnostics > Configuration.  
  
```xml  
<system.serviceModel>  
  <diagnostics>  
```  
  
 Ustawienia diagnostyczne WCF dla aplikacji wirtualnej usług IIS hostowanej w sieci Web są włączane w jej pliku Web. config. Innym rozwiązaniem jest utworzenie pliku Web. config w podkatalogu w aplikacji.  Wybranie tej opcji powoduje zastosowanie ustawień do wszystkich usług w podkatalogu.  Aby zapewnić spójność ustawień diagnostycznych dla wszystkich usług w aplikacji, ustawienia powinny znajdować się w pliku Web. config w katalogu aplikacji, a nie w jednym z katalogów podrzędnych w aplikacji.  
  
### <a name="channels"></a>Kanały  
 Funkcja ETW umożliwia składnikom oprogramowania bezpośrednie śledzenie zdarzeń dla określonych odbiorców za pomocą kanałów. Na przykład możesz wysyłać zdarzenia dla administratorów systemu do jednego kanału i zdarzenia, które deweloperzy aplikacji powinni zachować do innego kanału. Kanały są nazywane i zarejestrowane w systemie Windows, aby umożliwić konsumentom Wyświetlanie zdarzeń kanału przy użyciu Podgląd zdarzeń.  
  
 Funkcja śledzenia analitycznego dla programu WCF w [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] zapisów w kanale Microsoft-Windows-Application-Server-Applications. Ten kanał jest przeznaczony specjalnie dla użytkowników, którzy chcą monitorować kondycję usług WCF w środowisku produkcyjnym. Definiuje mały zestaw zdarzeń, które mogą być używane w wielu scenariuszach monitorowania kondycji i rozwiązywania problemów.  
  
 Aby włączyć śledzenie zdarzeń dla manifestu systemu Windows, tak aby komunikaty były zdekodowane prawidłowo w dzienniku zdarzeń, użyj narzędzia ServiceModelReg w wierszu polecenia w następujący sposób:  
  
 `ServiceModelReg.exe -i -c:etw`  
  
### <a name="dynamic-configuration"></a>Konfiguracja dynamiczna  
 Infrastruktura ETW umożliwia śledzenie i konfigurowanie ich dynamicznie przy użyciu standardowych narzędzi systemu Windows. Aby uzyskać więcej informacji, zobacz [dynamiczne Włączanie śledzenia analitycznego](dynamically-enabling-analytic-tracing.md).  
  
### <a name="message-flow-tracing"></a>Śledzenie przepływu komunikatów  
 Aby uzyskać więcej informacji na temat włączania śledzenia przepływu komunikatów, zobacz [Konfigurowanie śledzenia przepływu](configuring-message-flow-tracing.md)komunikatów.  
  
### <a name="keywords"></a>Słowa kluczowe  
 Słowa kluczowe służą do filtrowania komunikatów śledzenia i definiowania składnika .NET Framework emitowanego przez zdarzenie. Aby uzyskać więcej informacji, zobacz [dynamiczne Włączanie śledzenia analitycznego](dynamically-enabling-analytic-tracing.md).
