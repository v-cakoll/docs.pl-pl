---
title: Oprogramowanie .NET Core i Open-Source
ms.date: 03/30/2017
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
ms.openlocfilehash: bed5bb6aad5f3e651f7c4c0651a2365f17eb8a0b
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635294"
---
# <a name="net-core-and-open-source"></a>Platforma .NET Core i oprogramowanie open source

Ten artykuł zawiera krótkie omówienie tego, czym jest program .NET Core i pokazuje, jak można znaleźć więcej informacji. Aby znaleźć pełną listę dokumentacji dla platformy .NET Core, odwiedź [przewodnik po rdzeniu .NET](../../core/index.yml).

## <a name="what-is-net-core"></a>Co to jest .NET Core?  

.NET Core jest implementacją standardu .NET ogólnego przeznaczenia, modułowego, wieloplatformowego i open source. Zawiera wiele tych samych interfejsów API co .NET Framework (ale .NET Core jest mniejszy zestaw) i zawiera środowisko uruchomieniowe, framework, kompilator i składniki narzędzi, które obsługują różne systemy operacyjne i cele układu. Implementacja .NET Core była przede wszystkim napędzana przez obciążenia ASP.NET Core, ale także przez potrzebę i chęć bardziej nowoczesnej implementacji. Może być używany w scenariuszach urządzenia, chmury i osadzonych/IoT.  
  
Aby rozpocząć korzystanie z programu .NET Core, odwiedź samouczek .NET [Hello World w 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro).  
  
Główne cechy .NET Core to:
  
- **Wieloplatformowe:** .NET Core zapewnia kluczowe funkcje do implementowania funkcji aplikacji, których potrzebujesz, i ponownego użycia tego kodu, niezależnie od docelowego obiektu platformy. Obecnie obsługuje trzy główne systemy operacyjne (OS): Windows, Linux i macOS. Można pisać aplikacje i biblioteki, które działają niezmodyfikowane w obsługiwanych systemach operacyjnych. Aby wyświetlić listę obsługiwanych systemów operacyjnych, odwiedź stronę [.NET Core roadmap](https://github.com/dotnet/core/blob/master/roadmap.md).
  
- **Open source:** .NET Core jest jednym z wielu projektów pod kierownictwem [.NET Foundation](https://www.dotnetfoundation.org/) i jest dostępny na [GitHub](https://github.com/).  Posiadanie .NET Core jako projektu open source promuje bardziej przejrzysty proces rozwoju i promuje aktywną i zaangażowaną społeczność.  
  
- **Elastyczne wdrażanie:** istnieją dwa główne sposoby wdrażania aplikacji: wdrożenie zależne od struktury lub samodzielne wdrożenie. W ramach wdrożenia zależnego od struktury są zainstalowane tylko zależności aplikacji i innych firm, a aplikacja zależy od wersji systemu .NET Core, która ma być obecna. W przypadku samodzielnego wdrażania wersja .NET Core używana do tworzenia aplikacji jest również wdrażana wraz z zależnościami aplikacji i innych firm i może działać obok innych wersji. Aby uzyskać więcej informacji, zobacz [.NET Core Application Deployment](../../core/deploying/index.md).

- **Modułowy:** .NET Core jest modułowy, ponieważ jest wydany przez NuGet w mniejszych pakietach montażowych. Zamiast jednego dużego zestawu, który zawiera większość podstawowych funkcji, .NET Core jest dostępny jako mniejsze, zorientowane na funkcje pakiety. Ta modułowość umożliwia bardziej elastyczny model programowania dla nas i pozwala zoptymalizować aplikację, aby uwzględnić tylko pakiety NuGet, których potrzebujesz. Korzyści wynikające z mniejszej powierzchni aplikacji obejmują ściślejsze zabezpieczenia, zmniejszoną obsługę, lepszą wydajność i niższe koszty w modelu płatności za to, co używasz.  
  
## <a name="the-net-core-platform"></a>Platforma .NET Core
  
Platforma .NET Core składa się z kilku składników, w tym kompilatorów zarządzanych, środowiska wykonawczego, bibliotek klas podstawowych i wielu modeli aplikacji, takich jak ASP.NET Core. Możesz dowiedzieć się więcej o różnych składnikach i zaangażować się, odwiedzając następujące repozytoria [GitHub:](https://github.com/)  
  
- [.NET Core strona główna](https://github.com/dotnet/core)  
  
- [Środowisko uruchomieniowe — platforma core i środowisko uruchomieniowe .NET Core](https://github.com/dotnet/runtime)  
  
- [CLI — narzędzia wiersza polecenia .NET Core](https://github.com/dotnet/cli)  
  
- [Roslyn - platforma kompilatora .NET](https://github.com/dotnet/roslyn)  
  
- [ASP.NET Core](https://github.com/dotnet/aspnetcore)  
  
## <a name="see-also"></a>Zobacz też

- [.NET tutorial - Hello World w 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)
- [Przewodnik platformy .NET Core](../../core/index.yml)
- [dokumenty ASP.NET Core](/aspnet/core/)
