---
title: Programowanie przy użyciu zestawów i domen aplikacji
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 216766a8d8f120594c7d6dd1fd192f90b775c1d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="programming-with-application-domains-and-assemblies"></a>Programowanie przy użyciu zestawów i domen aplikacji
Hosty, takich jak Microsoft Internet Explorer, ASP.NET i obciążenia powłoki Windows środowisko uruchomieniowe języka wspólnego do procesu tworzenia [domeny aplikacji](../../../docs/framework/app-domains/application-domains.md) w tym przetwarzania i następnie załadowanie i wykonanie kodu użytkownika w tej domenie aplikacji podczas uruchamiania aplikacji .NET Framework. W większości przypadków nie trzeba martwić tworzenia domeny aplikacji i ładowanie zestawów do nich, ponieważ host czasu wykonywania wykonuje te zadania.  
  
 Jednak w przypadku tworzenia aplikacji, która będzie obsługiwać środowiska CLR, utworzenie narzędzia lub kod, który chcesz zwolnić programowo, lub podłączany składników, które może być zwolnione i ponownie załadowany na bieżąco, zostanie utworzony własne domeny aplikacji. Nawet jeśli host czasu wykonywania nie są tworzone, ta sekcja zawiera ważne informacje na temat pracy z zestawów załadowanych w tych domenach aplikacji i domen aplikacji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje dotyczące zestawów i domen aplikacji](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 Zawiera łącza do wszystkich — tematy porad znajdującego się w dokumentacji koncepcyjnego do programowania za pomocą zestawów i domen aplikacji.  
  
 [Używanie domen aplikacji](../../../docs/framework/app-domains/use.md)  
 Przykłady tworzenie, konfigurowanie i używanie domeny aplikacji.  
  
 [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 Opisuje sposób tworzenia, zaloguj się i ustawić atrybuty zestawów.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Emitowanie dynamicznych metod i zestawów](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 Opisuje sposób tworzenia zestawów dynamicznych.  
  
 [Zestawy w środowisku uruchomieniowym CLR](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Omówienie koncepcyjne zestawów.  
  
 [Domeny aplikacji](../../../docs/framework/app-domains/application-domains.md)  
 Omówienie koncepcyjne domen aplikacji.  
  
 [Odbicie — omówienie](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Informacje dotyczące używania **odbicia** klasę, aby uzyskać informacje o zestawie.
