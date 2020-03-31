---
title: Co nowego w umyka . NET Standard
description: W tym artykule podsumowano nowe funkcje i ulepszenia znalezione w każdej nowej wersji programu .NET Standard.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 28d6a3546e08bbc3a7d4a26f08ba9cc5e16a901b
ms.sourcegitcommit: 2ff49dcf9ddf107d139b4055534681052febad62
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2020
ms.locfileid: "80438202"
---
# <a name="whats-new-in-net-standard"></a>Co nowego w umyka . NET Standard

.NET Standard to formalna specyfikacja, która definiuje wersjonatowany zestaw interfejsów API, które muszą być dostępne w implementacjach platformy .NET zgodnych z tą wersją standardu. Program .NET Standard jest przeznaczony dla deweloperów bibliotek. Biblioteka przeznaczona dla wersji .NET Standard może być używana w dowolnej implementacji platformy .NET Framework, .NET Core lub Xamarin, która obsługuje tę wersję standardu.

Program .NET Standard jest dołączony do rdzenia SDK .NET, a także z programem Visual Studio po wybraniu obciążenia .NET Core.

## <a name="supported-net-implementations"></a>Obsługiwane implementacje platformy .NET

.NET Standard 2.0 jest obsługiwany przez następujące implementacje .NET:

- .NET Core 2.0 lub nowszy
- .NET Framework 4.6.1 lub nowsze
- Mono 5.4 lub nowsze
- Xamarin.iOS 10.14 lub nowsze
- Xamarin.Mac 3.8 lub nowsze
- Xamarin.Android 8.0 lub nowsze
- Uniwersalna platforma systemu Windows 10.0.16299 lub nowsza

## <a name="whats-new-in-net-standard-20"></a>Co nowego w .NET Standard 2.0

Program .NET Standard 2.0 zawiera następujące nowe funkcje:

### <a name="a-vastly-expanded-set-of-apis"></a>Znacznie rozszerzony zestaw interfejsów API

W wersji 1.6 program .NET Standard zawierał stosunkowo mały podzbiór interfejsów API. Wśród wykluczonych było wiele interfejsów API, które były powszechnie używane w .NET Framework lub platformy Xamarin. To komplikuje rozwój, ponieważ wymaga, aby deweloperzy znaleźć odpowiednie zamienniki dla znanych interfejsów API podczas tworzenia aplikacji i bibliotek, które są przeznaczone dla wielu implementacji platformy .NET. Program .NET Standard 2.0 rozwiązuje to ograniczenie, dodając ponad 20 000 więcej interfejsów API niż w standardzie .NET Standard 1.6, poprzedniej wersji standardu. Aby uzyskać listę interfejsów API, które zostały dodane do programu .NET Standard 2.0, zobacz [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).

Niektóre dodatki do obszaru <xref:System> nazw w .NET Standard 2.0 obejmują:

- Wsparcie dla <xref:System.AppDomain> klasy.
- Lepsza obsługa pracy z tablicami od <xref:System.Array> dodatkowych członków w klasie.
- Lepsza obsługa pracy z atrybutami <xref:System.Attribute> od dodatkowych członków w klasie.
- Lepsza obsługa kalendarza i <xref:System.DateTime> dodatkowe opcje formatowania wartości.
- Dodatkowa <xref:System.Decimal> funkcja zaokrąglania.
- Dodatkowe funkcje <xref:System.Environment> w klasie.
- Zwiększona kontrola nad modułem <xref:System.GC> zbierającym elementy bezużyteczne za pośrednictwem klasy.
- Ulepszona obsługa porównywania ciągów, wyliczania <xref:System.String> i normalizacji w klasie.
- Obsługa regulacji czasu letniego i <xref:System.TimeZoneInfo.AdjustmentRule> czasów <xref:System.TimeZoneInfo.TransitionTime> przejścia w klasach i.
- Znacznie zwiększona funkcjonalność w <xref:System.Type> klasie.
- Lepsza obsługa deserializacji obiektów wyjątków przez dodanie <xref:System.Runtime.Serialization.SerializationInfo> <xref:System.Runtime.Serialization.StreamingContext> konstruktora wyjątków z i parametrów.

### <a name="support-for-net-framework-libraries"></a>Obsługa bibliotek programu .NET Framework

Przeważająca większość bibliotek docelowych .NET Framework, a nie .NET Standard. Jednak większość wywołań w tych bibliotekach są interfejsy API, które są zawarte w .NET Standard 2.0. Począwszy od platformy .NET Standard 2.0, można uzyskać dostęp do bibliotek programu .NET Framework z biblioteki .NET Standard przy użyciu [podkładki zgodności](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification). Ta warstwa zgodności jest przezroczysta dla deweloperów; nie musisz nic robić, aby korzystać z bibliotek .NET Framework.

Jednym wymaganiem jest, że interfejsy API wywoływane przez bibliotekę klas .NET Framework muszą być uwzględnione w .NET Standard 2.0.

### <a name="support-for-visual-basic"></a>Obsługa języka Visual Basic

Teraz można tworzyć biblioteki .NET Standard w języku Visual Basic. Visual Studio 2019 i Visual Studio 2017 w wersji 15.3 lub nowszej z zainstalowanym obciążeniem .NET Core zawierają szablon biblioteki klas standardowych platformy .NET. W przypadku deweloperów języka Visual Basic, którzy używają innych narzędzi i środowisk programistycznych, można użyć nowego polecenia [dotnet](../../core/tools/dotnet-new.md) do utworzenia projektu biblioteki standardowej platformy .NET. Aby uzyskać więcej informacji, zobacz [obsługę narzędzi dla bibliotek .NET Standard](#tooling-support-for-net-standard-libraries).

### <a name="tooling-support-for-net-standard-libraries"></a>Obsługa narzędzi dla bibliotek standardowych platformy .NET

Wraz z wydaniem platformy .NET Core 2.0 i .NET Standard 2.0 zarówno program Visual Studio 2017, jak i [.NET Core CLI](../../core/tools/index.md) obejmują obsługę narzędzi do tworzenia bibliotek .NET Standard.

W przypadku instalowania programu Visual Studio z **wieloplatformowym** obciążeniem programowym .NET Core można utworzyć projekt biblioteki .NET Standard 2.0 przy użyciu szablonu projektu, jak pokazano na poniższym rysunku:

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C #](#tab/csharp)

![Dodawanie nowego projektu biblioteki standardu .NET](./media/std-project-cs.png)

Jeśli używasz interfejsu wiersza polecenia .NET Core, następujące polecenie [dotnet new](../../core/tools/dotnet-new.md) tworzy projekt biblioteki klas, który jest przeznaczony dla platformy .NET Standard 2.0:

```dotnetcli
dotnet new classlib
```

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

![Dodawanie nowego projektu biblioteki standardu .NET](./media/std-project-vb.png)

Jeśli używasz interfejsu wiersza polecenia .NET Core, następujące polecenie [dotnet new](../../core/tools/dotnet-new.md) tworzy projekt biblioteki klas, który jest przeznaczony dla platformy .NET Standard 2.0:

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a>Zobacz też

- [.NET Standard](../net-standard.md)
- [Przedstawiamy standard .NET](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
