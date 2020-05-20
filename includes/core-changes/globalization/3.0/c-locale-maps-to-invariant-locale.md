---
ms.openlocfilehash: c0551fa086644497c631cd9b6d7058398ff9ccfa
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702288"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a>Ustawienia regionalne "C" są mapowane na niezmienne ustawienia regionalne

Program .NET Core 2,2 i jego wcześniejsze wersje zależą od domyślnego zachowania ICU, które mapuje ustawienia regionalne "C" na ustawienia regionalne en_US_POSIX. En_US_POSIX locale ma niepożądane zachowanie sortowania, ponieważ nie obsługuje porównywania ciągów bez uwzględniania wielkości liter. Ponieważ niektóre dystrybucje systemu Linux ustawiają ustawienia regionalne "C" jako domyślne ustawienia regionalne, użytkownicy mieli nieoczekiwane zachowanie.

#### <a name="change-description"></a>Zmień opis

Począwszy od platformy .NET Core 3,0, mapowanie ustawień regionalnych "C" zostało zmienione tak, aby używało niezmiennej ustawień regionalnych zamiast en_US_POSIX. Ustawienia regionalne "C" do mapowania niezmiennej są również stosowane do systemu Windows w celu zapewnienia spójności.

Mapowanie "C" na en_US_POSIX kulturę powodowało pomyłkę klienta, ponieważ en_US_POSIX nie obsługuje operacji wyszukiwania ciągów z uwzględnieniem wielkości liter. Ponieważ ustawienia regionalne "C" są używane jako domyślne ustawienia regionalne dla niektórych dystrybucje systemu Linux, klienci napotykali to niepożądane zachowanie w tych systemach operacyjnych.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Niczego nie ma więcej niż świadomość tej zmiany. Ta zmiana dotyczy tylko aplikacji, które korzystają z mapowania ustawień regionalnych "C".

#### <a name="category"></a>Kategoria

Globalizacja

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Ta zmiana ma wpływ na wszystkie interfejsy API sortowania i kultury.

<!--

#### Affected APIs

-->
