---
title: Co nowego w programie .NET Standard
description: W tym artykule podsumowano nowe funkcje i ulepszenia dostępne w każdej nowej wersji programu .NET Standard.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
ms.openlocfilehash: a90df0360211c3b02f4f2d8697890180099c5807
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "76921060"
---
# <a name="whats-new-in-the-net-standard"></a>Co nowego w programie .NET Standard

Standard .NET jest formalną specyfikacją, która definiuje wersjonowany zestaw interfejsów API, które muszą być dostępne w implementacjach .NET, które są zgodne z tą wersją standardu. Standard .NET jest przeznaczony dla deweloperów biblioteki. Biblioteka przeznaczona dla wersji .NET Standard może być używana w dowolnej implementacji .NET Framework, .NET Core lub Xamarin, która obsługuje tę wersję standardu.

Najnowsza wersja standardu .NET to 2.0. Jest on dołączony do .NET Core 2.0 SDK, a także do programu Visual Studio 2017 w wersji 15.3 z zainstalowanym obciążeniem .NET Core.

## <a name="supported-net-implementations"></a>Obsługiwane implementacje .NET

Standard .NET 2.0 jest obsługiwany przez następujące implementacje .NET:

- .NET Core 2.0 lub nowszy
- .NET Framework 4.6.1 lub nowszy
- Mono 5.4 lub nowszy
- Xamarin.iOS 10.14 lub nowszy
- Xamarin.Mac 3.8 lub nowszy
- Xamarin.Android 8.0 lub nowszy
- Uniwersalna platforma systemu Windows 10.0.16299 lub nowsza

## <a name="whats-new-in-the-net-standard-20"></a>Co nowego w standardzie .NET 2.0

.NET Standard 2.0 zawiera następujące nowe funkcje:

### <a name="a-vastly-expanded-set-of-apis"></a>Znacznie rozszerzony zestaw interfejsów API

W wersji 1.6 standard .NET zawierał stosunkowo mały podzbiór interfejsów API. Wśród wykluczonych było wiele interfejsów API, które były powszechnie używane w .NET Framework lub Xamarin. Komplikuje to rozwój, ponieważ wymaga, aby deweloperzy znaleźć odpowiednie zamienniki dla znanych interfejsów API podczas tworzenia aplikacji i bibliotek, które są przeznaczone dla wielu implementacji .NET. .NET Standard 2.0 rozwiązuje to ograniczenie, dodając ponad 20 000 więcej interfejsów API niż były dostępne w .NET Standard 1.6, poprzedniej wersji standardu. Aby uzyskać listę interfejsów API dodanych do standardu .NET Standard 2.0, zobacz [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).

Niektóre dodatki do <xref:System> obszaru nazw w .NET Standard 2.0 obejmują:

- Wsparcie dla <xref:System.AppDomain> klasy.
- Lepsza obsługa pracy z tablicami z <xref:System.Array> dodatkowych elementów członkowskich w klasie.
- Lepsza obsługa pracy z atrybutami z <xref:System.Attribute> dodatkowych członków w klasie.
- Lepsza obsługa kalendarza i dodatkowe <xref:System.DateTime> opcje formatowania wartości.
- Dodatkowa <xref:System.Decimal> funkcja zaokrąglania.
- Dodatkowe funkcje w <xref:System.Environment> klasie.
- Zwiększona kontrola nad modułodśmie pamięci za pośrednictwem <xref:System.GC> klasy.
- Zwiększona obsługa porównywania ciągów, wyliczania i normalizacji w <xref:System.String> klasie.
- Obsługa regulacji czasu letniego i czasów <xref:System.TimeZoneInfo.AdjustmentRule> przejścia <xref:System.TimeZoneInfo.TransitionTime> w klasach i.
- Znacznie ulepszona <xref:System.Type> funkcjonalność w klasie.
- Lepsza obsługa deserializacji obiektów wyjątków przez dodanie <xref:System.Runtime.Serialization.SerializationInfo> <xref:System.Runtime.Serialization.StreamingContext> konstruktora wyjątku z parametrami i parametrami.

### <a name="support-for-net-framework-libraries"></a>Obsługa bibliotek programu .NET Framework

Zdecydowana większość bibliotek jest docelowa dla .NET Framework zamiast .NET Standard. Jednak większość wywołań w tych bibliotekach są do interfejsów API, które są zawarte w .NET Standard 2.0. Począwszy od .NET Standard 2.0, można uzyskać dostęp do bibliotek .NET Framework z biblioteki .NET Standard przy użyciu [podkładki zgodności](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification). Ta warstwa zgodności jest niewidoczna dla deweloperów; nie trzeba nic robić, aby skorzystać z bibliotek .NET Framework.

Pojedyncze wymaganie polega na tym, że interfejsy API wywoływane przez bibliotekę klas .NET Framework muszą być uwzględnione w standardzie .NET 2.0.

### <a name="support-for-visual-basic"></a>Obsługa języka Visual Basic

Teraz można tworzyć biblioteki standardów .NET w języku Visual Basic. W przypadku deweloperów języka Visual Basic korzystających z programu Visual Studio 2017 w wersji 15.3 lub nowszej z zainstalowanym obciążeniem .NET Core program Visual Studio zawiera teraz szablon standardowej biblioteki klas .NET. Dla deweloperów języka Visual Basic, którzy używają innych narzędzi programistycznych i środowisk, można użyć [polecenia dotnet new](../../core/tools/dotnet-new.md) do utworzenia projektu biblioteki standardowej .NET. Aby uzyskać więcej informacji, zobacz [obsługę narzędzi dla bibliotek standardów .NET](#tooling-support-for-net-standard-libraries).

### <a name="tooling-support-for-net-standard-libraries"></a>Obsługa narzędzi dla bibliotek standardów .NET

Wraz z wydaniem .NET Core 2.0 i .NET Standard 2.0 zarówno visual studio 2017, jak i [procesor cli .NET Core](../../core/tools/index.md) obsługują tworzenie bibliotek .NET Standard.

W przypadku instalowania programu Visual Studio z wieloplatformowym obciążeniem **programistycznym .NET Core** można utworzyć projekt biblioteki .NET Standard 2.0 przy użyciu szablonu projektu, jak pokazano na poniższej ilustracji:

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C #](#tab/csharp)

![Dodawanie nowego projektu biblioteki standardu .NET](./media/std-project-cs.png)

Jeśli używasz polecenia cli .NET Core, następujące [polecenie dotnet tworzy](../../core/tools/dotnet-new.md) projekt biblioteki klas, który jest przeznaczony dla .NET Standard 2.0:

```dotnetcli
dotnet new classlib
```

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

![Dodawanie nowego projektu biblioteki standardu .NET](./media/std-project-vb.png)

Jeśli używasz polecenia cli .NET Core, następujące [polecenie dotnet tworzy](../../core/tools/dotnet-new.md) projekt biblioteki klas, który jest przeznaczony dla .NET Standard 2.0:

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a>Zobacz też

- [.NET Standard](../net-standard.md)
- [Wprowadzenie do standardu .NET](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
