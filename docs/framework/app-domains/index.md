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
ms.openlocfilehash: 7124b6b234601e3afc27109ac318f47e3fe40c35
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675354"
---
# <a name="programming-with-application-domains-and-assemblies"></a>Programowanie przy użyciu zestawów i domen aplikacji
Tworzenie hostów, takich jak Microsoft Internet Explorer, ASP.NET i ładowanie powłoki Windows środowiska uruchomieniowego języka wspólnego w procesie [domeny aplikacji](../../../docs/framework/app-domains/application-domains.md) tego przetwarzania i następnie załadować i wykonywanie kodu użytkownika w tej domenie aplikacji podczas uruchamiania aplikacji .NET Framework. W większości przypadków nie trzeba martwić się o sposobie tworzenia domeny aplikacji i ładowanie zestawów do nich, ponieważ host środowiska uruchomieniowego wykonuje te zadania.  
  
 Jednak jeśli tworzysz aplikację, która będzie obsługiwać środowisko uruchomieniowe języka wspólnego, utworzenie narzędzi lub kod, który chcesz zwolnić programowo, lub podłączanych składników, które może być zwolniony i ponownie załadowany na bieżąco, zostanie utworzona własne domeny aplikacji. Nawet wtedy, gdy host środowiska uruchomieniowego są nietworzenie, ta sekcja zawiera ważne informacje na temat pracy z domenami aplikacji i zestawy, ładowane w tych domenach aplikacji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje dotyczące zestawów i domen aplikacji](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 Zawiera łącza do wszystkich tematów instrukcje w dokumentacji koncepcyjnego dla programowania, korzystając z domeny aplikacji i zestawy.  
  
 [Używanie domen aplikacji](../../../docs/framework/app-domains/use.md)  
 Przykłady tworzenia, konfigurowania i używania domen aplikacji.  
  
 [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 W tym artykule opisano sposób tworzenia, zaloguj się i ustawianie atrybutów zestawów.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Emitowanie dynamicznych metod i zestawów](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 W tym artykule opisano sposób tworzenia zestawów dynamicznych.  
  
 [Zestawy w środowisku uruchomieniowym CLR](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Omówienie koncepcyjne zestawów.  
  
 [Domeny aplikacji](../../../docs/framework/app-domains/application-domains.md)  
 Omówienie koncepcyjne domen aplikacji.  
  
 [Omówienie odbicia](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Opisuje sposób używania **odbicia** klasy, aby uzyskać informacje o zestawie.
