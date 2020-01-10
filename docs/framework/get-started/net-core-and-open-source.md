---
title: Oprogramowanie .NET Core i Open-Source
ms.date: 03/30/2017
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
ms.openlocfilehash: 4032ba771d917d25473c8de350cc752bd052f94d
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75752548"
---
# <a name="net-core-and-open-source"></a>.NET Core i Open Source

Ten artykuł zawiera krótkie omówienie platformy .NET Core i pokazuje, jak można znaleźć więcej informacji. Aby znaleźć pełną listę dokumentacji programu .NET Core, zapoznaj się z [przewodnikiem dotyczącym platformy .NET Core](../../core/index.md).
  
<a name="BKMK_WhatisNETCore"></a>   
## <a name="what-is-net-core"></a>Co to jest platforma .NET Core?  
 .NET Core to implementacja ogólna, modularna, międzyplatformowa i typu open source .NET Standard. Zawiera wiele z tych samych interfejsów API, co .NET Framework (ale platforma .NET Core jest mniejszym zestawem) i obejmuje składniki środowiska uruchomieniowego, platformy, kompilatora i narzędzi, które obsługują różne systemy operacyjne i elementy docelowe układów. Implementacja platformy .NET Core była przede wszystkim oparta na ASP.NET Core obciążeniach, ale także potrzeb i chęci posiadania bardziej nowoczesnej implementacji. Może być używany w scenariuszach dotyczących urządzeń, chmury i osadzonych/IoT.  
  
 Aby rozpocząć pracę z platformą .NET Core, odwiedź Samouczek platformy .NET [Hello World w ciągu 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro).  
  
Główne cechy platformy .NET Core to:
  
- **Międzyplatformowe:** platforma .NET Core zapewnia kluczowe funkcje do implementowania potrzebnych funkcji aplikacji i ponownego użycia tego kodu niezależnie od miejsca docelowego platformy. Obecnie obsługuje trzy główne systemy operacyjne: Windows, Linux i macOS. Można napisać aplikacje i biblioteki, które są uruchamiane niezmodyfikowane w obsługiwanych systemach operacyjnych. Aby wyświetlić listę obsługiwanych systemów operacyjnych, przejdź do [przewodnika po platformie .NET Core](https://github.com/dotnet/core/blob/master/roadmap.md).
  
- **Open Source:** .NET Core to jeden z wielu projektów w ramach Stewardship [.NET Foundation](https://www.dotnetfoundation.org/) i dostępny w serwisie [GitHub](https://github.com/).  Posiadanie platformy .NET Core jako projektu typu open source promuje bardziej przejrzysty proces opracowywania i promuje aktywną i zaangażowaną społeczność.  
  
- **Elastyczne wdrożenie:** istnieją dwa podstawowe sposoby wdrażania aplikacji: wdrożenie zależne od platformy lub wdrożenie samodzielne. W przypadku wdrażania zależnego od platformy są instalowane tylko aplikacje i zależności innych firm, a aplikacja zależy od wersji platformy .NET Core, która ma być obecna.  W przypadku wdrażania z dowolnego siebie, wersja platformy .NET Core używana do kompilowania aplikacji również jest wdrażana wraz z aplikacją i zależnościami innych firm i może być uruchamiana równolegle z innymi wersjami.    Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji .NET Core](../../core/deploying/index.md).

- **Modułowy:** .NET Core jest modułem modularnym, ponieważ jest on wydawany przez NuGet w mniejszych pakietach zestawu. Zamiast jednego dużego zestawu, który zawiera większość podstawowych funkcji, środowisko .NET Core jest udostępniane jako mniejsze pakiety skoncentrowane na funkcjach. Umożliwia to wydajniejszy model programistyczny dla nas i pozwala zoptymalizować aplikację w taki sposób, aby zawierała tylko potrzebne pakiety NuGet. Zalety mniejszej powierzchni aplikacji obejmują ściślejsze zabezpieczenia, ograniczoną obsługę, lepszą wydajność i obniżenie kosztów w modelu płatność za rzeczywiste użycie.  
  
## <a name="the-net-core-platform"></a>Platforma .NET Core
  
Platforma .NET Core składa się z kilku składników, takich jak zarządzane kompilatory, środowisko uruchomieniowe, biblioteki klas podstawowych i liczne modele aplikacji, takie jak ASP.NET Core. Aby dowiedzieć się więcej na temat różnych składników i skorzystać z następujących repozytoriów usługi [GitHub](https://github.com/) :  
  
- [Strona główna platformy .NET Core](https://github.com/dotnet/core)  
  
- [Środowisko uruchomieniowe — platforma .NET Core i środowisko uruchomieniowe](https://github.com/dotnet/runtime)  
  
- [Interfejs wiersza polecenia platformy .NET Core Tools](https://github.com/dotnet/cli)  
  
- [Roslyn — .NET Compiler Platform](https://github.com/dotnet/roslyn)  
  
- [ASP.NET Core](https://github.com/dotnet/aspnetcore)  
  
## <a name="see-also"></a>Zobacz także

- [Samouczek platformy .NET — Hello world w ciągu 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)
- [Przewodnik po programie .NET Core](../../core/index.md)
- [Dokumentacja ASP.NET Core](/aspnet/core/)
