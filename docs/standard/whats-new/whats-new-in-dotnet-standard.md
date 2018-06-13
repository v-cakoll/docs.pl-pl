---
title: Co to jest nowa w programie .NET Standard
description: W tym artykule przedstawiono nowe funkcje i ulepszenia znajdujące się w każdej nowej wersji programu .NET Standard.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e422e6ff65439d105020a6305b66a8192586a8f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591492"
---
# <a name="whats-new-in-the-net-standard"></a>Co to jest nowa w programie .NET Standard

.NET Standard jest formalną specyfikację, który definiuje wersjonowany zestaw interfejsów API, które muszą być dostępne na implementacje .NET, które są zgodne z tą wersją standardowego. .NET Standard jest przeznaczona dla deweloperów biblioteki. Biblioteka, przeznaczonego dla wersji platformy .NET Standard może służyć wykonania dowolnego .NET Framework .NET Core i Xamarin obsługuje tej wersji standard.

Najnowszą wersję programu .NET Standard jest wersja 2.0. Jest dostępna przy użyciu zestawu SDK programu .NET Core 2.0, a także z programu Visual Studio 2017 wersji 15 ustęp 3 z obciążeniem .NET Core zainstalowane.

## <a name="supported-net-implementations"></a>Obsługiwane implementacje .NET

.NET 2.0 standardowe jest obsługiwany przez następujące implementacje .NET:

- Oprogramowanie .NET core 2.0 lub nowszy
- .NET framework 4.6.1 lub nowszej
- Mono 5.4 lub nowszy
- Xamarin.iOS 10.14 lub nowszy
- Xamarin.Mac 3.8 lub nowszej
- Xamarin.Android 8.0 lub nowszej
- Platforma uniwersalna systemu Windows 10.0.16299 lub nowszy

## <a name="whats-new-in-the-net-standard-20"></a>Co to jest nowa w programie .NET 2.0 standardowe

Standardowa .NET 2.0 obejmuje następujące nowe funkcje:

### <a name="a-vastly-expanded-set-of-apis"></a>Znacząco rozwinięte zestaw interfejsów API

Za pomocą wersji 1.6 .NET Standard uwzględnione stosunkowo mały podzbiór interfejsów API. Między tymi wyłączone zostały wiele interfejsów API, które często używane w programie .NET Framework lub Xamarin. Komplikuje rozwoju, ponieważ wymaga ona, że deweloperzy znaleźć odpowiednie elementy zastępcze znanych interfejsów API podczas opracowywania aplikacji i bibliotek przeznaczonych do wiele implementacji .NET. .NET 2.0 standardowe usuwa to ograniczenie, dodając ponad 20 000 API więcej niż były dostępne w .NET Standard 1.6 poprzedniej wersji standard. Listę interfejsów API, które zostały dodane do programu .NET 2.0 standardowego, zobacz [.NET 2.0 standardowe vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).

Niektóre dodatki do <xref:System> przestrzeni nazw w .NET Standard 2.0 obejmują:

- Obsługa <xref:System.AppDomain> klasy.
- Lepszą obsługę pracy z tablicami z dodatkowych członków w <xref:System.Array> klasy.
- Lepszą obsługę pracy z atrybutów z dodatkowych członków w <xref:System.Attribute> klasy.
- Lepiej kalendarza pomocy technicznej i dodatkowe opcje formatowania <xref:System.DateTime> wartości.
- Dodatkowe <xref:System.Decimal> funkcji zaokrąglania.
- Dodatkowe funkcje w <xref:System.Environment> klasy.
- Ulepszone kontrolę nad modułu zbierającego elementy bezużyteczne za pośrednictwem <xref:System.GC> klasy.
- Rozszerzona obsługa porównania ciągów, wyliczenia i normalizacji w <xref:System.String> klasy.
- Obsługa Uwzględniaj dostosowań i czasy przejścia w <xref:System.TimeZoneInfo.AdjustmentRule> i <xref:System.TimeZoneInfo.TransitionTime> klasy.
- Znacznie rozszerzoną funkcjonalność w <xref:System.Type> klasy.
- Lepszą obsługę deserializacji obiektów wyjątku przez dodanie wyjątku konstruktora z <xref:System.Runtime.Serialization.SerializationInfo> i <xref:System.Runtime.Serialization.StreamingContext> parametrów.

### <a name="support-for-net-framework-libraries"></a>Obsługa bibliotek .NET Framework

Przeważająca większość bibliotek docelowy .NET Framework, a nie .NET Standard. Do interfejsów API, które znajdują się w .NET 2.0 standardowe są jednak większość wywołań w tych bibliotek. Począwszy od programu .NET 2.0 standardowe dostępnych bibliotek .NET Framework z biblioteki .NET Standard za pomocą [podkładki zgodności](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification). Ta warstwa zgodności jest niewidoczny dla deweloperów; nie trzeba wykonywać żadnych czynności, aby móc korzystać z biblioteki .NET Framework.

Pojedynczy wymagane jest, że interfejsy API o nazwie w bibliotece klas programu .NET Framework muszą być zawarte w standardowe .NET 2.0.

### <a name="support-for-visual-basic"></a>Obsługa języka Visual Basic

Można teraz tworzyć .NET standardowych bibliotek języka Visual Basic. Dla deweloperów języka Visual Basic, za pomocą programu Visual Studio 2017 wersji 15 ustęp 3 lub nowszym z obciążenia .NET Core zainstalowane Visual Studio teraz obejmuje szablonu standardowa biblioteka klas programu .NET. Dla deweloperów języka Visual Basic, korzystających z innych narzędzi do tworzenia i środowisk, można użyć [dotnet nowe](../../core/tools/dotnet-new.md) polecenie, aby utworzyć projekt biblioteki standardowej .NET. Aby uzyskać więcej informacji, zobacz [Obsługa narzędzi dla platformy .NET standardowych bibliotek](#tooling-support-for-net-standard-libraries).

### <a name="tooling-support-for-net-standard-libraries"></a>Obsługa narzędzi dla platformy .NET standardowych bibliotek

Wraz z wydaniem programu .NET Core 2.0 i .NET 2.0 standardowe, zarówno programu Visual Studio 2017 i [.NET Core interfejsu wiersza polecenia (CLI)](../../core/tools/index.md) obejmują narzędzia pomocy technicznej do tworzenia bibliotek .NET Standard.

Jeśli zainstalujesz program Visual Studio z **aplikacji dla wielu platform .NET Core** obciążenie, można utworzyć projektu biblioteki .NET 2.0 standardowe za pomocą szablonu projektu, jak przedstawiono na poniższym rysunku:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

![Dodaj nowy .NET Standard projektu biblioteki](./media/std-project-cs.png)

W przypadku korzystania z platformy .NET Core interfejsu wiersza polecenia, następujące [dotnet nowe](../../core/tools/dotnet-new.md) polecenie tworzy projektu biblioteki klas, przeznaczonego dla programu .NET 2.0 standardowe:

```
dotnet new classlib
```

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

![Dodaj nowy .NET Standard projektu biblioteki](./media/std-project-vb.png)

W przypadku korzystania z platformy .NET Core interfejsu wiersza polecenia, następujące [dotnet nowe](../../core/tools/dotnet-new.md) polecenie tworzy projektu biblioteki klas, przeznaczonego dla programu .NET 2.0 standardowe:

```
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a>Zobacz także

[.NET Standard](../net-standard.md)  
[Wprowadzenie do platformy .NET Standard](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)
