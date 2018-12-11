---
title: Jak przechowywanie wersji zestawu .NET Core SDK zmieniło się
description: W tym artykule opisano, jak przechowywanie wersji zestawu .NET Core SDK i środowisko uruchomieniowe zmieniło się w przedziale czasu wersja 2.1.
ms.date: 07/26/2018
ms.custom: seodec18
ms.openlocfilehash: e4b87d2ebd6dc5a0d5b874dc35dcaf746fdd4a0a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131134"
---
# <a name="net-core-version-changes-between-10-and-21"></a>.NET Core w wersji zmiany między 1.0 i 2.1

Numery wersji dla platformy .NET Core to wyzwanie, ponieważ zestaw .NET Core SDK i środowisko uruchomieniowe programu .NET Core w wersji na inną odstępach czasu. Różne odstępach czasu oznaczają, że zespół wymuszono wykonaj tylko dwa spośród następujących czynności:

1. Wersja niezależnie, w szczególności, dzięki czemu narzędzia, C# i VB, aby awansować szybciej niż środowisko uruchomieniowe programu .NET Core.
2. Obsługa wyrównanie, numery wersji między .NET Core SDK i środowisko uruchomieniowe programu .NET Core.
3. Użyj semantyki przechowywania wersji dla platformy .NET Core SDK i środowisko uruchomieniowe programu .NET Core.

2.0.0 wymusić wyrównanie wersji i sprawnie zanalizować w jednej wersji. W grudniu 2017 r zestawu .NET Core SDK miał wersji funkcji, nie odpowiedniej wersji w środowisku uruchomieniowym .NET Core. Zespól cele 1 i 3, utraty wyrównanie między środowisko uruchomieniowe programu .NET Core i zestawu SDK. Różne wersje programu .NET Core SDK 2.1.x zostały wydane przed platformy .NET Core środowiska uruchomieniowego 2.1. Ponieważ zestaw SDK nie jest zgodny będzie przekazywać, te wersje zestawu SDK 2.1.x nie jest przeznaczona platformy .NET Core środowiska uruchomieniowego 2.1. Zespół odpowiedział na znaczną pomyłek, przełączając się cele 1 i 2, porzucenie semantycznego przechowywania wersji, zgodnie z opisem w [wersji platformy .NET Core](index.md#versioning-details).

Ze względu na czas decyzji, Porzuć wersji semantycznej wystąpiły przejściowe wydań w 2.1.10x i 2.1.20x wersji numer zakresy, które również nie można kierować platformy .NET Core środowiska uruchomieniowego 2.1.

Pierwsze dwie cyfry numery wersji dopasowania z 2.1.0 wersję środowiska uruchomieniowego programu .NET Core i 2.1.300 wersji programu .NET Core SDK.

Szczegółowe informacje o wersjach poszczególnych składników, w tym platformy i języka w wersji kompilatora, można znaleźć na [strony pobierania dla platformy .NET Core](https://www.microsoft.com/net/download/dotnet-core/current). Aby uzyskać szczegółowe informacje na temat poprzednich wersji, wybierz żądaną wersję z [pobierania .NET Core archiwa strony](https://www.microsoft.com/net/download/archives). Obsługa szczegółowych informacji można znaleźć w artykułów opisujących official będzie przydatna dla [.NET obsługuje zasady](https://www.microsoft.com/net/Support/Policy).