---
title: Zagadnienia dotyczące wersji i aktualizacji dla deweloperów języka C#
description: Wprowadzenie nowych funkcji języków w bibliotece może mieć wpływ na kod, który go używa.
ms.date: 09/19/2018
ms.openlocfilehash: 3ffe2f6fd64a391fddf28233dccb022c95851884
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399386"
---
# <a name="version-and-update-considerations-for-c-developers"></a>Zagadnienia dotyczące wersji i aktualizacji dla deweloperów języka C#

Zgodność jest bardzo ważnym celem, ponieważ nowe funkcje są dodawane do języka C#. W prawie wszystkich przypadkach istniejący kod można ponownie skompilować z nową wersją kompilatora bez żadnego problemu.

Podczas przyjmowania nowych funkcji języka w bibliotece może być wymagana większa ostrożność. Być może tworzysz nową bibliotekę z funkcjami znalezionymi w najnowszej wersji i musisz upewnić się, że aplikacje utworzone przy użyciu poprzednich wersji kompilatora mogą z niej korzystać. Możesz też uaktualnić istniejącą bibliotekę, a wielu użytkowników może nie mieć jeszcze uaktualnionych wersji. Podejmując decyzje dotyczące przyjmowania nowych funkcji, musisz wziąć pod uwagę dwie odmiany zgodności: kompatybilność ze źródłem i zgodna z plikami binarnymi.

## <a name="binary-compatible-changes"></a>Zmiany zgodne z binarnymi

Zmiany w bibliotece są **zgodne z plikami binarnymi,** gdy zaktualizowana biblioteka może być używana bez odbudowy aplikacji i bibliotek, które jej używają. Zestawy zależne nie są wymagane do przebudowy, ani nie są wymagane żadne zmiany kodu źródłowego. Zmiany zgodne z binarnymi są również źródłem zmian zgodnych.

## <a name="source-compatible-changes"></a>Zmiany zgodne ze źródłem

Zmiany w bibliotece są **zgodne ze źródłem,** gdy aplikacje i biblioteki korzystające z biblioteki nie wymagają zmian kodu źródłowego, ale źródło musi zostać ponownie skompilowane względem nowej wersji, aby działała poprawnie.

## <a name="incompatible-changes"></a>Niekompatybilne zmiany

Jeśli zmiana nie jest **zgodna ze źródłem** ani **zgodnym z plikami binarnymi,** zmiany kodu źródłowego wraz z ponowną kompilacją są wymagane w bibliotekach zależnych i aplikacjach.

## <a name="evaluate-your-library"></a>Ocena biblioteki

Te pojęcia zgodności wpływają na publiczne i chronione deklaracje dla biblioteki, a nie jej implementacji wewnętrznej. Przyjęcie jakichkolwiek nowych funkcji wewnętrznie są zawsze **binarne kompatybilne**.  

Zmiany **zgodne z plikami binarnymi** zapewniają nową składnię, która generuje ten sam skompilowany kod dla deklaracji publicznych, co starsza składnia. Na przykład zmiana metody na element członkowski zabudowany wyrażenie jest zmiana **zgodna z binarnymi:**

Oryginalny kod:

```csharp
public double CalculateSquare(double value)
{
    return value * value;
}
```

Nowy kod:

```csharp
public double CalculateSquare(double value) => value * value;
```

**Zmiany zgodne ze źródłem** wprowadzają składnię, która zmienia skompilowany kod dla publicznego elementu członkowskiego, ale w sposób zgodny z istniejącymi witrynami wywołań. Na przykład zmiana podpisu metody z parametru według wartości na `in` parametr odniesienia jest zgodna ze źródłem, ale nie zgodna z plikami binarnymi:

Oryginalny kod:

```csharp
public double CalculateSquare(double value) => value * value;
```

Nowy kod:

```csharp
public double CalculateSquare(in double value) => value * value;
```

[Co nowego](index.md) artykułu zanotować, jeśli wprowadzenie funkcji, która wpływa na deklaracje publiczne jest zgodne ze źródłem lub binarne zgodne.
