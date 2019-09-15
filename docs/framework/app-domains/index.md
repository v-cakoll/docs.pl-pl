---
title: Programowanie przy użyciu zestawów i domen aplikacji
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4f0c2ad1290a7f9cf8d0c43c504a3e0a9628b86
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971924"
---
# <a name="programming-with-application-domains-and-assemblies"></a>Programowanie przy użyciu zestawów i domen aplikacji
Hosty, takie jak Microsoft Internet Explorer, ASP.NET i powłoka systemu Windows, ładują środowisko uruchomieniowe języka wspólnego do procesu, tworzą w tym procesie [domenę aplikacji](../../../docs/framework/app-domains/application-domains.md) , a następnie ładują i wykonują kod użytkownika w tej domenie aplikacji podczas uruchamiania programu .NET Aplikacja struktury. W większości przypadków nie trzeba martwić się o tworzenie domen aplikacji i ładowaniem do nich zestawów, ponieważ host środowiska uruchomieniowego wykonuje te zadania.  
  
 Jeśli jednak tworzysz aplikację, która będzie hostować środowisko uruchomieniowe języka wspólnego, tworzysz narzędzia lub kod, który chcesz usunąć programowo, lub utworzyć podłączane składniki, które mogą zostać zwolnione i ponownie załadowane na bieżąco, będziesz tworzyć własne domeny aplikacji. Nawet jeśli nie tworzysz hosta środowiska uruchomieniowego, ta sekcja zawiera ważne informacje dotyczące pracy z domenami i zestawami aplikacji załadowanymi w tych domenach aplikacji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje dotyczące zestawów i domen aplikacji](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 Zawiera łącza do wszystkich tematów, które znajdują się w dokumentacji koncepcyjnej dotyczącej programowania przy użyciu domen i zestawów aplikacji.  
  
 [Używanie domen aplikacji](../../../docs/framework/app-domains/use.md)  
 Zawiera przykłady tworzenia, konfigurowania i używania domen aplikacji.  
  
 [Programowanie za pomocą zestawów](../../standard/assembly/program.md)  
 Opisuje sposób tworzenia, podpisywania i ustawiania atrybutów dla zestawów.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Emitowanie dynamicznych metod i zestawów](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 Opisuje sposób tworzenia zestawów dynamicznych.  
  
 [Zestawy w środowisku .NET](../../standard/assembly/index.md)  
 Omówienie koncepcyjne zestawów.  
  
 [Domeny aplikacji](../../../docs/framework/app-domains/application-domains.md)  
 Omówienie koncepcyjne domen aplikacji.  
  
 [Przegląd odbicia](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Opisuje sposób użycia klasy **odbicia** w celu uzyskania informacji o zestawie.
