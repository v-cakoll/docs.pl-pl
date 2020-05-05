---
ms.openlocfilehash: d35de48dd22003c851cf5dba9e8517ec48b9217b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567782"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a>Ustawienia regionalne "C" są mapowane na niezmienne ustawienia regionalne

Program .NET Core 2,2 i jego wcześniejsze wersje zależą od domyślnego zachowania ICU, które mapuje ustawienia regionalne "C" na ustawienia regionalne en_US_POSIX. En_US_POSIX locale ma niepożądane zachowanie sortowania, ponieważ nie obsługuje porównywania ciągów bez uwzględniania wielkości liter. Ponieważ niektóre dystrybucje systemu Linux ustawiają ustawienia regionalne "C" jako domyślne ustawienia regionalne, użytkownicy mieli nieoczekiwane zachowanie.

#### <a name="change-description"></a>Zmień opis

Począwszy od platformy .NET Core 3,0, mapowanie ustawień regionalnych "C" zostało zmienione tak, aby używało niezmiennej ustawień regionalnych zamiast en_US_POSIX. Ustawienia regionalne "C" do mapowania niezmiennej są również stosowane do systemu Windows w celu zapewnienia spójności.

Mapowanie "C" na en_US_POSIX kulturę powodowało pomyłkę klienta, ponieważ en_US_POSIX nie obsługuje operacji wyszukiwania ciągów z uwzględnieniem wielkości liter. Ponieważ ustawienia regionalne "C" są używane jako domyślne ustawienia regionalne dla niektórych dystrybucje systemu Linux, klienci napotykali to niepożądane zachowanie w tych systemach operacyjnych.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

### <a name="recommended-action"></a>Zalecana akcja

Niczego nie ma więcej niż świadomość tej zmiany. Ta zmiana dotyczy tylko aplikacji, które korzystają z mapowania ustawień regionalnych "C".

### <a name="category"></a>Kategoria

Globalizacja

### <a name="affected-apis"></a>Dotyczy interfejsów API

Ta zmiana ma wpływ na wszystkie interfejsy API sortowania i kultury.

<!--

-->
