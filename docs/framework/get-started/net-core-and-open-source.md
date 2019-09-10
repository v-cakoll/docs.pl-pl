---
title: Oprogramowanie .NET Core i Open-Source
ms.date: 03/30/2017
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2ad74a70fff9916dc66bb4d2eacbdaf40cb241c3
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70853949"
---
# <a name="net-core-and-open-source"></a>Oprogramowanie .NET Core i Open-Source
Ten temat zawiera krótkie omówienie platformy .NET Core i pokazuje, jak można znaleźć więcej informacji. Aby zapoznać się z pełną listą tematów dotyczących platformy .NET Core, zapoznaj się z [przewodnikiem dotyczącym platformy .NET Core](../../core/index.md).
  
<a name="BKMK_WhatisNETCore"></a>   
## <a name="what-is-net-core"></a>Co to jest .NET Core?  
 .NET Core to implementacja ogólna, modularna, międzyplatformowa i typu open source .NET Standard. Zawiera wiele z tych samych interfejsów API, co .NET Framework (ale platforma .NET Core jest mniejszym zestawem) i obejmuje składniki środowiska uruchomieniowego, platformy, kompilatora i narzędzi, które obsługują różne systemy operacyjne i elementy docelowe układów. Implementacja platformy .NET Core była przede wszystkim oparta na ASP.NET Core obciążeniach, ale także potrzeb i chęci posiadania bardziej nowoczesnej implementacji. Może być używany w scenariuszach dotyczących urządzeń, chmury i osadzonych/IoT.  
  
 Aby rozpocząć pracę z platformą .NET Core, odwiedź Samouczek platformy .NET [Hello World w ciągu 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro).  
  
 Poniżej przedstawiono główne cechy platformy .NET Core:  
  
- **Międzyplatformowe:** platforma .NET Core zapewnia kluczowe funkcje do implementowania potrzebnych funkcji aplikacji i ponownego użycia tego kodu niezależnie od miejsca docelowego platformy. Obecnie obsługuje trzy główne systemy operacyjne: Windows, Linux i macOS. Można napisać aplikacje i biblioteki, które są uruchamiane niezmodyfikowane w obsługiwanych systemach operacyjnych. Aby wyświetlić listę obsługiwanych systemów operacyjnych, przejdź do [przewodnika po platformie .NET Core](https://github.com/dotnet/core/blob/master/roadmap.md).
  
- **Open Source:** .NET Core to jeden z wielu projektów w ramach Stewardship [.NET Foundation](https://www.dotnetfoundation.org/) i dostępny w serwisie [GitHub](https://github.com/).  Posiadanie platformy .NET Core jako projektu typu open source promuje bardziej przejrzysty proces opracowywania i promuje aktywną i zaangażowaną społeczność.  
  
- **Elastyczne wdrożenie:** istnieją dwa podstawowe sposoby wdrażania aplikacji: wdrożenie zależne od platformy lub wdrożenie samodzielne. W przypadku wdrażania zależnego od platformy są instalowane tylko aplikacje i zależności innych firm, a aplikacja zależy od wersji platformy .NET Core, która ma być obecna.  W przypadku wdrażania z dowolnego siebie, wersja platformy .NET Core używana do kompilowania aplikacji również jest wdrażana wraz z aplikacją i zależnościami innych firm i może być uruchamiana równolegle z innymi wersjami.    Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji .NET Core](../../core/deploying/index.md).

- **Modułowy:** .NET Core jest modułem modularnym, ponieważ jest on wydawany przez NuGet w mniejszych pakietach zestawu. Zamiast jednego dużego zestawu, który zawiera większość podstawowych funkcji, środowisko .NET Core jest udostępniane jako mniejsze pakiety skoncentrowane na funkcjach. Umożliwia to wydajniejszy model programistyczny dla nas i pozwala zoptymalizować aplikację w taki sposób, aby zawierała tylko potrzebne pakiety NuGet. Zalety mniejszej powierzchni aplikacji obejmują ściślejsze zabezpieczenia, ograniczoną obsługę, lepszą wydajność i obniżenie kosztów w modelu płatność za rzeczywiste użycie.  
  
## <a name="the-net-core-platform"></a>Platforma .NET Core  
 Platforma .NET Core zawiera kilka składników, takich jak zarządzane kompilatory, środowisko uruchomieniowe, biblioteki klas podstawowych i liczne modele aplikacji, takie jak ASP.NET Core. Aby dowiedzieć się więcej na temat różnych składników i korzystać z nich, należy odwiedzić następujące repozytoria [GitHub](https://github.com/) :  
  
- [.NET Core](https://github.com/dotnet/core)  
  
- [CoreFX — podstawowe biblioteki platformy .NET](https://github.com/dotnet/corefx)  
  
- [CoreCLR — środowisko uruchomieniowe platformy .NET Core](https://github.com/dotnet/coreclr)  
  
- [Interfejs wiersza polecenia platformy .NET Core Tools](https://github.com/dotnet/cli)  
  
- [Roslyn — .NET Compiler Platform](https://github.com/dotnet/roslyn)  
  
- [ASP.NET Core](https://github.com/aspnet/home)  
  
## <a name="see-also"></a>Zobacz także

- [Samouczek platformy .NET — Hello world w ciągu 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)
- [Przewodnik platformy .NET Core](../../core/index.md)
- [Dokumentacja ASP.NET Core](/aspnet/core/)
