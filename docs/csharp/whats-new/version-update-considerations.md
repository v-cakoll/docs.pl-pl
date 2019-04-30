---
title: Wersja i zaktualizuj uwagi dla deweloperów języka C#
description: Wprowadzenie do nowych funkcji języków w bibliotece może wpłynąć na kod, który korzysta z niego.
ms.date: 09/19/2018
ms.openlocfilehash: 56685422e2c73dcca25acbdccb3a77a8de9df775
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675510"
---
# <a name="version-and-update-considerations-for-c-developers"></a>Wersja i zaktualizuj uwagi dla deweloperów języka C#

Zgodność jest bardzo ważne cel w miarę dodawania nowych funkcji języka C#. Prawie we wszystkich przypadkach istniejący kod może ponownie kompilowana do nowej wersji kompilatora bez żadnych problemu.

Ostrożnie mogą być wymagane, gdy przyjmują nowe funkcje języka w bibliotece. Jego przy użyciu funkcji, które znajdują się w najnowszej wersji tworzy nową bibliotekę i należy do zagwarantowania, że aplikacje utworzone przy użyciu poprzedniej wersji kompilatora może być użyty. Lub może być uaktualniania istniejącej biblioteki i wielu użytkowników może nie uaktualniono wersje jeszcze. Przy podejmowaniu decyzji o przyjęcie nowych funkcji, należy wziąć pod uwagę dwie odmiany zgodność: źródłowy zgodny i zgodne dane binarne.

## <a name="binary-compatible-changes"></a>Binarny zmiany zgodne

Zmiany w bibliotece są **zgodne dane binarne** gdy zaktualizowano biblioteki mogą być używane w taki sposób, bez ponowne tworzenie aplikacji i bibliotek, które go używają. Zależne zestawy nie są wymagane do można odbudować ani nie są wymagane zmiany kodu źródłowego. Binarny zgodne nie są zgodne zmiany źródła.

## <a name="source-compatible-changes"></a>Zmiany zgodne źródło

Zmiany w bibliotece są **zgodne źródło** po aplikacji i bibliotek, korzystających z biblioteki nie wymagają zmiany kodu źródłowego, ale źródło powodującej względem nowej wersji, aby działać poprawnie.

## <a name="incompatible-changes"></a>Niezgodne zmiany

Jeśli zmiany nie jest ani **zgodne źródło** ani **zgodne dane binarne**, zmiany kodu źródłowego oraz ponownej kompilacji są wymagane w aplikacjach i zależne biblioteki.

## <a name="evaluate-your-library"></a>Oceń biblioteki

Te pojęcia zgodności wpływają na deklaracje publiczne i chronione, biblioteki, a nie wewnętrzną implementację. Wewnętrznie przyjęcie żadnych nowych funkcji są zawsze **zgodne dane binarne**.  

**Binarny zgodnego** zmiany Podaj nową składnię, która generuje ten sam kod skompilowany dla deklaracji na publiczny jako starsza składnia. Na przykład zmiana metody do elementu członkowskiego z wyrażeniem w treści jest **zgodne dane binarne** zmiany:

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

**Zgodne źródło** zmiany wprowadzają składnia, która zmienia kod skompilowany członka publicznego, ale w sposób zgodny z istniejących witryn wywołania. Na przykład zmiana sygnatury metody z przez wartość parametru, aby `in` przez odwołanie parametr jest zgodne, źródła, ale nie binarne zgodnych:

Oryginalny kod:

```csharp
public double CalculateSquare(double value) => value * value;
```

Nowy kod:

```csharp
public double CalculateSquare(in double value) => value * value;
```

[What's new](index.md) artykułów należy pamiętać, jeśli wprowadzenie do funkcji, który wpływa na publicznego deklaracje zgodnego źródła lub zgodne dane binarne.