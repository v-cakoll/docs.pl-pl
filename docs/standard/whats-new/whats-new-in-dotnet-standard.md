---
title: What's new in .NET Standard
description: Ten artykuł zawiera podsumowanie nowych funkcji i ulepszeń w każda nowa wersja programu .NET Standard.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8810508bc61f6fd625b1485f199249a96b2686e6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43674406"
---
# <a name="whats-new-in-the-net-standard"></a>What's new in .NET Standard

.NET Standard to formalną specyfikację, definiujący określonej wersji zestawu interfejsów API, które muszą być dostępne w implementacji .NET, które są zgodne z wersji standard. .NET Standard jest przeznaczona dla deweloperów bibliotek. Biblioteka, która jest przeznaczona dla wersji .NET Standard może służyć w .NET Framework, .NET Core i Xamarin implementacji, który obsługuje daną wersję standard.

Najnowszą wersję programu .NET Standard jest w wersji 2.0. Znajduje się za pomocą zestawu .NET Core 2.0 SDK, a także za pomocą programu Visual Studio 2017 w wersji 15.3 z zainstalowanym obciążeniem platformy .NET Core.

## <a name="supported-net-implementations"></a>Obsługiwane implementacje platformy .NET

.NET Standard 2.0 jest obsługiwany przez następujące implementacje platformy .NET:

- .NET core 2.0 lub nowszej
- Program .NET framework 4.6.1 lub nowszej
- Narzędzie mono 5.4 lub nowszy
- Xamarin.iOS 10.14 lub nowszy
- Platforma Xamarin.Mac 3,8 lub nowszy
- Platforma Xamarin.Android w wersji 8.0 lub nowszej
- Universal Windows Platform 10.0.16299 lub nowszej

## <a name="whats-new-in-the-net-standard-20"></a>What's new in .NET Standard 2.0

.NET Standard 2.0 obejmuje następujące nowe funkcje:

### <a name="a-vastly-expanded-set-of-apis"></a>Znacznie rozwinięty zestaw interfejsów API

Za pomocą wersji 1.6 .NET Standard uwzględnione stosunkowo małego podzbioru interfejsów API. Wśród tych wykluczonych były wiele interfejsów API, które często używane w programie .NET Framework lub Xamarin. Ten komplikuje rozwoju, ponieważ wymaga ona, czy deweloperów Znajdź odpowiednie elementy zastępcze dobrze znanych interfejsów API, podczas ich tworzenia aplikacji i bibliotek przeznaczonych do wielu implementacjach systemu .NET. .NET Standard 2.0 dotyczy to ograniczenie, dodając ponad 20 000 więcej interfejsów API nie były dostępne w .NET Standard w wersji 1.6, poprzednią wersję standard. Aby uzyskać listę interfejsów API, które zostały dodane do platformy .NET Standard 2.0, zobacz [vs .NET Standard 2.0 w wersji 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).

Niektóre dodatki do <xref:System> przestrzeni nazw w programie .NET Standard 2.0 obejmują:

- Obsługa <xref:System.AppDomain> klasy.
- Lepsza obsługa pracy z tablicami z dodatkowe elementy członkowskie w <xref:System.Array> klasy.
- Lepsza obsługa pracy z atrybutami dodatkowe elementy członkowskie w <xref:System.Attribute> klasy.
- Lepiej kalendarza pomocy technicznej i dodatkowe opcje formatowania dla <xref:System.DateTime> wartości.
- Dodatkowe <xref:System.Decimal> zaokrąglania funkcji.
- Dodatkowe funkcje w <xref:System.Environment> klasy.
- Rozszerzony kontrolę nad moduł odśmiecania pamięci, za pośrednictwem <xref:System.GC> klasy.
- Rozszerzoną obsługę porównania ciągów, wyliczenia i normalizacji w <xref:System.String> klasy.
- Obsługa Uwzględniaj dostosowań i czasów przejścia w <xref:System.TimeZoneInfo.AdjustmentRule> i <xref:System.TimeZoneInfo.TransitionTime> klasy.
- Znacznie rozszerzone funkcje w <xref:System.Type> klasy.
- Lepsza obsługa deserializacji obiektów wyjątków przez dodanie konstruktora wyjątków z <xref:System.Runtime.Serialization.SerializationInfo> i <xref:System.Runtime.Serialization.StreamingContext> parametrów.

### <a name="support-for-net-framework-libraries"></a>Obsługa bibliotek .NET Framework

Przeważająca większość bibliotek docelowe z .NET Framework, a nie .NET Standard. Jednak większość wywołań w tych bibliotek są do interfejsów API, które stanowią część pakietu .NET Standard 2.0. Począwszy od .NET Standard 2.0, dostępne biblioteki .NET Framework z biblioteki .NET Standard za pomocą [podkładki zgodności](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-20/README.md#assembly-unification). Ta warstwa zgodności jest niewidoczne dla deweloperów; nie trzeba wykonywać żadnych czynności, aby móc korzystać z biblioteki .NET Framework.

Jednym wymaganiem jest o tym, czy interfejsy API o nazwie w bibliotece klas programu .NET Framework, muszą być zawarte w .NET Standard 2.0.

### <a name="support-for-visual-basic"></a>Obsługa języka Visual Basic

Możesz teraz tworzyć biblioteki .NET Standard w języku Visual Basic. Dla deweloperów programu Visual Basic, za pomocą programu Visual Studio 2017 w wersji 15.3 lub nowszym z zainstalowanym obciążeniem platformy .NET Core Visual Studio zawiera obecnie szablon Biblioteka klas programu .NET Standard. Dla deweloperów języka Visual Basic, którzy korzystają z innych narzędzi programistycznych i środowisk, możesz użyć [dotnet nowe](../../core/tools/dotnet-new.md) polecenie, aby utworzyć projekt Biblioteka .NET Standard. Aby uzyskać więcej informacji, zobacz [narzędzia obsługujące biblioteki .NET Standard](#tooling-support-for-net-standard-libraries).

### <a name="tooling-support-for-net-standard-libraries"></a>Obsługę narzędzi dla biblioteki .NET Standard

Wersja programu .NET Core 2.0 i .NET Standard 2.0, zarówno program Visual Studio 2017 i [.NET Core interfejsu wiersza polecenia (CLI)](../../core/tools/index.md) obejmują narzędzia do obsługi do tworzenia biblioteki .NET Standard.

Po zainstalowaniu programu Visual Studio z **programowanie dla wielu platform .NET Core** obciążenia, można utworzyć projekt biblioteki .NET Standard 2.0 przy użyciu szablonu projektu, jak przedstawiono na poniższym rysunku:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

![Dodaj projekt biblioteki nowe .NET Standard](./media/std-project-cs.png)

Jeśli używasz platformy .NET Core interfejsu wiersza polecenia, następujące [dotnet nowe](../../core/tools/dotnet-new.md) polecenie tworzy projekt biblioteki klas, który jest przeznaczony dla .NET Standard 2.0:

```
dotnet new classlib
```

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

![Dodaj projekt biblioteki nowe .NET Standard](./media/std-project-vb.png)

Jeśli używasz platformy .NET Core interfejsu wiersza polecenia, następujące [dotnet nowe](../../core/tools/dotnet-new.md) polecenie tworzy projekt biblioteki klas, który jest przeznaczony dla .NET Standard 2.0:

```
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a>Zobacz także

[.NET Standard](../net-standard.md)  
[Wprowadzenie do platformy .NET Standard](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)
