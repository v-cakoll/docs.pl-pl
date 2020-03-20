---
title: Programowanie przy użyciu zestawów i domen aplikacji
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
ms.openlocfilehash: 2c849d27c70971d17bf4359ee7ae1081ee976a5f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73119821"
---
# <a name="programming-with-application-domains-and-assemblies"></a>Programowanie przy użyciu zestawów i domen aplikacji

Hosty, takie jak Microsoft Internet Explorer, ASP.NET i powłoki systemu Windows, ładują środowisko uruchomieniowe wspólnego języka do procesu, tworzą [domenę aplikacji](application-domains.md) w tym procesie, a następnie ładują i wykonaj kod użytkownika w tej domenie aplikacji podczas uruchamiania aplikacji .NET Framework. W większości przypadków nie trzeba się martwić o tworzenie domen aplikacji i ładowanie zestawów do nich, ponieważ host środowiska wykonawczego wykonuje te zadania.  
  
Jeśli jednak tworzysz aplikację, która będzie obsługiwać środowisko uruchomieniowe języka wspólnego, tworzenie narzędzi lub kodu, które chcesz rozładować programowo, lub tworzenie podłączanych składników, które mogą być rozładowywane i przeładowywane na bieżąco, będziesz tworzyć własne domen aplikacji. Nawet jeśli nie tworzysz hosta środowiska uruchomieniowego, ta sekcja zawiera ważne informacje dotyczące sposobu pracy z domenami aplikacji i zestawami załadowanymi w tych domenach aplikacji.  
  
## <a name="in-this-section"></a>W tej sekcji  

[Porady dotyczące zestawów i domen aplikacji](application-domains-and-assemblies-how-to-topics.md)  
Zawiera łącza do wszystkich tematów inkoncesjowych znalezionych w dokumentacji koncepcyjnej do programowania z domen aplikacji i zestawów.  
  
[Używanie domeny aplikacji](use.md)  
Zawiera przykłady tworzenia, konfigurowania i używania domen aplikacji.  
  
[Programowanie za pomocą zestawów](../../standard/assembly/program.md)  
W tym artykule opisano sposób tworzenia, podpisywania i ustawiania atrybutów w zestawach.  
  
## <a name="related-sections"></a>Sekcje pokrewne  

[Emitowanie dynamicznych metod i zestawów](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
Opisuje sposób tworzenia zestawów dynamicznych.  
  
[Zestawy w środowisku .NET](../../standard/assembly/index.md)  
Omówienie koncepcyjne zestawów.  
  
[Domeny aplikacji](application-domains.md)  
Omówienie koncepcyjne domen aplikacji.  
  
[Przegląd refleksji](../reflection-and-codedom/reflection.md)  
Opisuje sposób korzystania **z Reflection** klasy, aby uzyskać informacje o zestawie.
