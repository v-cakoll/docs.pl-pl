---
title: Co nowego w programie .NET Standard
description: Ten artykuł zawiera podsumowanie nowych funkcji i ulepszeń znalezionych w każdej nowej wersji .NET Standard.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
ms.openlocfilehash: ebf656c4a5499fff54cb5a70a93c4e8cc9c82d0a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73101758"
---
# <a name="whats-new-in-the-net-standard"></a>Co nowego w programie .NET Standard

.NET Standard to formalna Specyfikacja, która definiuje zestaw interfejsów API, które muszą być dostępne w implementacjach platformy .NET, które są zgodne z tą wersją Standard. .NET Standard jest przeznaczona dla deweloperów biblioteki. Biblioteka, która jest przeznaczona dla wersji .NET Standard, może być używana w ramach implementacji .NET Framework, .NET Core lub Xamarin, która obsługuje tę wersję Standard.

Najnowsza wersja .NET Standard to 2,0. Jest on zawarty w zestawie SDK platformy .NET Core 2,0, a także z programem Visual Studio 2017 w wersji 15,3 z zainstalowanym obciążeniem programu .NET Core.

## <a name="supported-net-implementations"></a>Obsługiwane implementacje platformy .NET

.NET Standard 2,0 jest obsługiwana przez następujące implementacje .NET:

- .NET Core 2,0 lub nowszy
- .NET Framework 4.6.1 lub nowsze
- Mono 5,4 lub nowszy
- Platforma Xamarin. iOS 10,14 lub nowsza
- Platforma Xamarin. Mac 3,8 lub nowsza
- Platforma Xamarin. Android 8,0 lub nowsza
- Platforma uniwersalna systemu Windows 10.0.16299 lub nowszy

## <a name="whats-new-in-the-net-standard-20"></a>Co nowego w .NET Standard 2,0

.NET Standard 2,0 zawiera następujące nowe funkcje:

### <a name="a-vastly-expanded-set-of-apis"></a>Zestaw interfejsów API o szerokim rozszerzeniu

W wersji 1,6, .NET Standard obejmowały niewielki podzbiór interfejsów API. Wśród tych wykluczonych było wiele interfejsów API, które były często używane w .NET Framework lub Xamarin. To komplikuje programowanie, ponieważ wymaga, aby deweloperzy znalazły odpowiednie zamienniki dla znanych interfejsów API podczas opracowywania aplikacji i bibliotek przeznaczonych dla wielu implementacji platformy .NET. .NET Standard 2,0 dotyczy tego ograniczenia przez dodanie ponad 20 000 więcej interfejsów API niż w .NET Standard 1,6, poprzedniej wersji Standard. Aby uzyskać listę interfejsów API, które zostały dodane do .NET Standard 2,0, zobacz [.NET Standard 2,0 vs 1,6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).

Niektóre dodatki do przestrzeni nazw <xref:System> w .NET Standard 2,0 obejmują:

- Obsługa klasy <xref:System.AppDomain>.
- Lepsza obsługa pracy z tablicami z dodatkowych elementów członkowskich w klasie <xref:System.Array>.
- Lepsza obsługa pracy z atrybutami z dodatkowych elementów członkowskich w klasie <xref:System.Attribute>.
- Lepsza obsługa kalendarza i dodatkowe opcje formatowania dla wartości <xref:System.DateTime>.
- Dodatkowe funkcje zaokrąglania <xref:System.Decimal>.
- Dodatkowa funkcjonalność klasy <xref:System.Environment>.
- Rozszerzona kontrola nad modułem wyrzucania elementów bezużytecznych za pośrednictwem klasy <xref:System.GC>.
- Ulepszona obsługa porównywania ciągów, wyliczania i normalizacji w klasie <xref:System.String>.
- Obsługa zmian czasu letnich i czasów przejścia w klasach <xref:System.TimeZoneInfo.AdjustmentRule> i <xref:System.TimeZoneInfo.TransitionTime>.
- Znacznie rozszerzona funkcjonalność klasy <xref:System.Type>.
- Lepsza obsługa deserializacji obiektów wyjątków przez dodanie konstruktora wyjątków z parametrami <xref:System.Runtime.Serialization.SerializationInfo> i <xref:System.Runtime.Serialization.StreamingContext>.

### <a name="support-for-net-framework-libraries"></a>Obsługa bibliotek .NET Framework

Przeciążanie większości bibliotek celem .NET Framework, a nie .NET Standard. Większość wywołań w tych bibliotekach obejmuje jednak interfejsy API, które znajdują się w .NET Standard 2,0. Począwszy od .NET Standard 2,0, można uzyskać dostęp do bibliotek .NET Framework z biblioteki .NET Standard za pomocą [podkładki zgodności](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification). Ta warstwa zgodności jest niewidoczna dla deweloperów; nie trzeba wykonywać żadnych czynności, aby korzystać z bibliotek .NET Framework.

Jedynym wymaganiem jest, że interfejsy API wywoływane przez bibliotekę klas .NET Framework muszą być dołączone do .NET Standard 2,0.

### <a name="support-for-visual-basic"></a>Obsługa Visual Basic

Teraz można opracowywać biblioteki .NET Standard w Visual Basic. W przypadku Visual Basic deweloperów korzystających z programu Visual Studio 2017 w wersji 15,3 lub nowszej z zainstalowanym obciążeniem programu .NET Core program Visual Studio zawiera teraz szablon biblioteki klas .NET Standard. Dla Visual Basic deweloperów, którzy korzystają z innych narzędzi programistycznych i środowisk, można użyć polecenia [dotnet New](../../core/tools/dotnet-new.md) , aby utworzyć projekt biblioteki .NET Standard. Aby uzyskać więcej informacji, zobacz [Obsługa narzędzi dla bibliotek .NET Standard](#tooling-support-for-net-standard-libraries).

### <a name="tooling-support-for-net-standard-libraries"></a>Obsługa narzędzi dla bibliotek .NET Standard

W przypadku wersji programu .NET Core 2,0 i .NET Standard 2,0 zarówno program Visual Studio 2017, jak i [interfejs wiersza polecenia platformy .NET Core (CLI)](../../core/tools/index.md) zawierają narzędzia obsługujące tworzenie .NET Standard bibliotek.

W przypadku instalowania programu Visual Studio z użyciem obciążenia **międzyplatformowego platformy .NET Core** można utworzyć projekt biblioteki .NET Standard 2,0 przy użyciu szablonu projektu, tak jak pokazano na poniższej ilustracji:

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

![Dodaj nowy projekt biblioteki .NET Standard](./media/std-project-cs.png)

Jeśli używasz interfejs wiersza polecenia platformy .NET Core, następujące polecenie [dotnet New](../../core/tools/dotnet-new.md) powoduje utworzenie projektu biblioteki klas, który jest przeznaczony dla .NET Standard 2,0:

```dotnetcli
dotnet new classlib
```

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

![Dodaj nowy projekt biblioteki .NET Standard](./media/std-project-vb.png)

Jeśli używasz interfejs wiersza polecenia platformy .NET Core, następujące polecenie [dotnet New](../../core/tools/dotnet-new.md) powoduje utworzenie projektu biblioteki klas, który jest przeznaczony dla .NET Standard 2,0:

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a>Zobacz także

- [.NET Standard](../net-standard.md)
- [Wprowadzenie .NET Standard](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
