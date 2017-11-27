---
title: Wprowadzenie do programu .NET Framework
ms.custom: updateeachrelease
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- .NET Framework, getting started
- getting started [.NET Framework]
ms.assetid: c693fd34-88fe-4d90-b332-19eeadf3b7e7
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 66e581e04aa0c3d33fb1ef9a7f4163d131f625bf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="get-started-with-the-net-framework"></a>Wprowadzenie do programu .NET Framework

.NET Framework jest wykonanie środowiska zarządza aplikacji przeznaczonych programu .NET Framework. Składa się z środowisko uruchomieniowe języka wspólnego, co zapewnia zarządzanie pamięcią i innych usługach system i biblioteki szeroką gamę klasy, która umożliwia deweloperom korzystać z niezawodne, niezawodnego kodu dla wszystkich obszarów głównych tworzenia aplikacji.

<a name="Introducing"></a>
## <a name="what-is-the-net-framework"></a>Co to jest programu .NET Framework?

.NET Framework jest zarządzanego środowiska wykonawczego udostępniający wielu usług, do jego uruchomionej aplikacji. Składa się z dwóch głównych składników: środowisko uruchomieniowe języka wspólnego (CLR), która jest aparatem wykonywania, który obsługuje uruchamianie aplikacji i biblioteki klas .NET Framework, która zawiera bibliotekę przetestowane, kod wielokrotnego użytku, które mogą być wywoływane z własnej aplikacji. Usługi, które zapewnia uruchamianie aplikacji programu .NET Framework są następujące:

- Zarządzanie pamięcią. W wielu językach programowania programistów jest odpowiedzialny za przydzielanie i zwalnia pamięć i obsługa okresy istnienia obiektu. W aplikacjach .NET Framework środowisko CLR zapewnia tych usług w imieniu aplikacji.

- Wspólny system typów. W przypadku tradycyjnych języków programowania podstawowe typy są definiowane przez kompilator, co stwarza współdziałanie między językami. W programie .NET Framework podstawowe typy są definiowane przez system typów .NET Framework i są wspólne dla wszystkich języków, które odnoszą się do programu .NET Framework.

- Biblioteka klas szeroką gamę. Zamiast konieczności pisania czasach ogromne ilości kodu do obsługi wspólnej operacje na niskim poziomie programowania, programistów używać łatwo dostępne biblioteki typów i ich elementy członkowskie w bibliotece klas programu .NET Framework.

- Środowiska deweloperskie i technologii. .NET Framework zawiera biblioteki do określonych obszarów tworzenia aplikacji, takich jak ASP.NET dla aplikacji sieci web, ADO.NET dla dostępu do danych i Windows Communication Foundation zorientowane na usługę aplikacji.

- Współdziałanie języków. Kompilatory języka, które odnoszą się do programu .NET Framework Emituj kod pośredniego o nazwie wspólnej pośredniego języka (CIL), który z kolei jest kompilowana w czasie wykonywania przez środowisko uruchomieniowe języka wspólnego. Przy użyciu tej funkcji w jednym języku procedury są dostępne dla innych języków i programistów skupić się na tworzenie aplikacji w językach preferowany.

- Zgodność wersji. W rzadkich wyjątki aplikacje, które są tworzone przy użyciu określonej wersji programu .NET Framework uruchomienia bez żadnych modyfikacji w nowszej wersji.

- Wykonanie Side-by-side. .NET Framework pomaga rozwiązać konfliktów wersji, zezwalając wielu wersji plików wykonywalnych języka aby istnieje na tym samym komputerze. Oznacza to, że wiele wersji aplikacji mogą współistnieć i że aplikację można uruchomić od używanej wersji programu .NET Framework, z którego został utworzony. Wykonanie Side-by-side ma zastosowanie do grupy wersji .NET Framework 1.0/1.1, 2.0/3.0/3.5 i 4/4.5.x/4.6.x/4.7.x.

- Przeznaczanie dla wielu platform. Określając [.NET Standard](~/docs/standard/net-standard.md), deweloperom tworzenie zestawów działające na wielu platformach .NET Framework, takich jak Windows 7, Windows 8, Windows 8.1, Windows 10, Windows Phone i konsoli Xbox 360.

<a name="ForUsers"></a>
## <a name="the-net-framework-for-users"></a>.NET Framework dla użytkowników

Jeśli nie opracowywania aplikacji .NET Framework, ale można ich używać, trzeba nie ma informacji o jego operacji lub .NET Framework. W większości przypadków programu .NET Framework jest całkowicie niewidoczne dla użytkowników.

Jeśli używasz systemu operacyjnego, programu .NET Framework może być zainstalowany na tym komputerze. Ponadto po zainstalowaniu aplikacji, która wymaga programu .NET Framework, program instalacyjny aplikacji może zainstalować określonej wersji programu .NET Framework na komputerze. W niektórych przypadkach może wystąpić okno dialogowe z prośbą o Zainstaluj program .NET Framework. Jeśli właśnie próbowano uruchomić aplikację, gdy pojawi się okno dialogowe i, jeśli komputer ma dostęp do Internetu, można przejść do strony sieci Web, który umożliwia zainstalowanie Brak wersji programu .NET Framework.

Ogólnie rzecz biorąc nie należy odinstalować wersji programu .NET Framework, które są zainstalowane na tym komputerze. Istnieją dwa powody to:

- Jeśli używasz aplikacji zależy od określonej wersji programu .NET Framework, tej aplikacji może spowodować przerwanie usunięcie tej wersji.

- Niektóre wersje programu .NET Framework są aktualizacje w miejscu do wcześniejszych wersji. Na przykład [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] jest dostępna aktualizacja w miejscu do wersji 2.0 i .NET Framework 4.7.1 jest dostępna aktualizacja w miejscu do wersji 4, 4.6, 4.5, 4.5.2, 4.6.1, 4.5.1, 4.6.2 i 4.7. Aby uzyskać więcej informacji, zobacz [wersje programu .NET Framework i zależności](../../../docs/framework/migration-guide/versions-and-dependencies.md).

Jeśli zostanie wybrana opcja usunięcia programu .NET Framework, należy zawsze używać **programy i funkcje** z Panelu sterowania, aby go odinstalować. Nigdy nie ręcznie usuń wersję programu .NET Framework.

Należy pamiętać, że wiele wersji .NET Framework mogą współistnieć na jednym komputerze jednocześnie. Oznacza to, że nie masz do odinstalowania poprzednich wersji, aby zainstalować nowszą wersję.

<a name="ForDevelopers"></a> 
## <a name="the-net-framework-for-developers"></a>.NET Framework dla deweloperów

Jeśli jesteś deweloperem, wybierz język programowania, który obsługuje programu .NET Framework do tworzenia aplikacji. Ponieważ programu .NET Framework zapewnia niezależność od języka i współdziałanie, interakcji z innych aplikacji .NET Framework i składników, niezależnie od języka, z której zostały opracowane.

Do tworzenia aplikacji programu .NET Framework lub składników należy wykonać następujące czynności:

1. Jeśli nie jest preinstalowany na system operacyjny, należy zainstalować wersję programu .NET Framework, który będzie współpracować z aplikacji. Najbardziej aktualne wersje produkcji jest .NET Framework 4.7.1, który jest preinstalowany na systemu Windows 10 spadek twórców aktualizacji i jest dostępny do pobrania w starszych wersjach systemu operacyjnego Windows. Wymagania systemowe programu .NET Framework, można zobaczyć [wymagania systemowe](../../../docs/framework/get-started/system-requirements.md). Aby uzyskać informacje na temat instalowania innych wersji programu .NET Framework, zobacz [Przewodnik instalacji](../../../docs/framework/install/guide-for-developers.md). Dodatkowe pakiety .NET Framework są wydawane poza pasmem, co oznacza, że w przypadku wydane na podstawie stopniowego poza żadnych regularnych lub zaplanowanego cyklu. Aby uzyskać informacje na temat tych pakietów, zobacz [.NET Framework i poza harmonogramem](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md).

2. Wybierz język lub języki obsługiwane przez program .NET Framework, która ma być używany do opracowywania aplikacji. Dostępnych jest kilka języków, w tym Visual Basic, C#, Visual F # i C + +/ CLI firmy Microsoft. (Język programowania, który służy do opracowywania aplikacji dla programu .NET Framework jest zgodna [specyfikacji infrastruktury języka wspólnego (CLI)](http://go.microsoft.com/fwlink/?LinkId=199862).)

3. Wybierz i zainstaluj rozwoju środowiska do tworzenia aplikacji i który obsługuje z wybranego języka programowania lub języków. Microsoft zintegrowane środowisko programistyczne (IDE) dla aplikacji .NET Framework jest [programu Visual Studio](http://go.microsoft.com/fwlink/?LinkId=325532). Jest ona dostępna w numerze wersji.

Aby uzyskać więcej informacji na temat tworzenia aplikacji przeznaczonych dla platformy .NET Framework, zobacz [Podręcznik programowania](../../../docs/framework/development-guide.md).

## <a name="related-topics"></a>Tematy pokrewne

| Tytuł | Opis |
| ----- |------------ |
| [Omówienie](../../../docs/framework/get-started/overview.md) | Zawiera szczegółowe informacje dla deweloperów, którzy tworzą aplikacje kierowanych programu .NET Framework. |
| [Przewodnik instalacji](../../../docs/framework/install/index.md) | Informacje na temat Instalowanie programu .NET Framework. |  
| [.NET Framework i zwalnia poza pasmem](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md) | Zawiera opis programu .NET Framework poza harmonogramem i używania ich w aplikacji. |
| [Wymagania systemowe](../../../docs/framework/get-started/system-requirements.md) | Wymieniono wymagania sprzętowe i programowe dotyczące uruchamiania programu .NET Framework. |
| [Oprogramowanie .NET core i Open Source](../../../docs/framework/get-started/net-core-and-open-source.md) | W tym artykule opisano .NET Core w odniesieniu do programu .NET Framework oraz sposobu otwierania projektów platformy .NET Core open source. |
| [Dokumentacja platformy .NET core](https://docs.microsoft.com/dotnet/) | Udostępnia koncepcyjnej i dokumentacji interfejsu API dla platformy .NET Core. |

## <a name="see-also"></a>Zobacz także

[.NET framework — przewodnik](../../../docs/framework/index.md)   
[Nowości](../../../docs/framework/whats-new/index.md)   
[Przeglądarka interfejs API .NET](/dotnet/api/)   
[Podręcznik programowania](../../../docs/framework/development-guide.md)
