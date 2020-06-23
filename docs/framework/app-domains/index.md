---
title: Programowanie przy użyciu zestawów i domen aplikacji
description: Poznaj programowanie z domenami i zestawami aplikacji w programie .NET. Zobacz linki do tematów zawierających instrukcje & przykłady tworzenia domen aplikacji & zestawów.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
ms.openlocfilehash: 1c28fe0abeb279a1dbbc6dcf043c1780c72d79df
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903441"
---
# <a name="programming-with-application-domains-and-assemblies"></a>Programowanie przy użyciu zestawów i domen aplikacji

Hosty, takie jak Microsoft Internet Explorer, ASP.NET i powłoka systemu Windows, ładują środowisko uruchomieniowe języka wspólnego do procesu, tworzą w tym procesie [domenę aplikacji](application-domains.md) , a następnie ładują i wykonują kod użytkownika w tej domenie aplikacji podczas uruchamiania aplikacji .NET Framework. W większości przypadków nie trzeba martwić się o tworzenie domen aplikacji i ładowaniem do nich zestawów, ponieważ host środowiska uruchomieniowego wykonuje te zadania.  
  
Jeśli jednak tworzysz aplikację, która będzie hostować środowisko uruchomieniowe języka wspólnego, tworzysz narzędzia lub kod, który chcesz zwolnić programowo, lub tworząc podłączane składniki, które mogą zostać zwolnione i ponownie załadowane na bieżąco, będziesz tworzyć własne domeny aplikacji. Nawet jeśli nie tworzysz hosta środowiska uruchomieniowego, ta sekcja zawiera ważne informacje dotyczące pracy z domenami i zestawami aplikacji załadowanymi w tych domenach aplikacji.  
  
## <a name="in-this-section"></a>W tej sekcji  

[Porady dotyczące zestawów i domen aplikacji](application-domains-and-assemblies-how-to-topics.md)  
Zawiera łącza do wszystkich tematów, które znajdują się w dokumentacji koncepcyjnej dotyczącej programowania przy użyciu domen i zestawów aplikacji.  
  
[Używanie domeny aplikacji](use.md)  
Zawiera przykłady tworzenia, konfigurowania i używania domen aplikacji.  
  
[Programowanie za pomocą zestawów](../../standard/assembly/index.md)  
Opisuje sposób tworzenia, podpisywania i ustawiania atrybutów dla zestawów.  
  
## <a name="related-sections"></a>Sekcje pokrewne  

[Emitowanie dynamicznych metod i zestawów](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
Opisuje sposób tworzenia zestawów dynamicznych.  
  
[Zestawy w środowisku .NET](../../standard/assembly/index.md)  
Omówienie koncepcyjne zestawów.  
  
[Domeny aplikacji](application-domains.md)  
Omówienie koncepcyjne domen aplikacji.  
  
[Przegląd odbicia](../reflection-and-codedom/reflection.md)  
Opisuje sposób użycia klasy **odbicia** w celu uzyskania informacji o zestawie.
