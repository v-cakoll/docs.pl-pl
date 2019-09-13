---
ms.openlocfilehash: 9e9e443be9ea51d214e95c676fc28f0d8790af8b
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70930069"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a>Ustawienia regionalne "C" są mapowane na niezmienne ustawienia regionalne

Program .NET Core 2,2 i jego wcześniejsze wersje zależą od domyślnego zachowania ICU, które mapuje ustawienia regionalne "C" na ustawienia regionalne en_US_POSIX. Ustawienia regionalne en_US_POSIX mają niepożądane zachowanie sortowania, ponieważ nie obsługuje porównywania ciągów bez uwzględniania wielkości liter. Ponieważ niektóre dystrybucje systemu Linux ustawiają ustawienia regionalne "C" jako domyślne ustawienia regionalne, użytkownicy mieli nieoczekiwane zachowanie. 

#### <a name="details"></a>Szczegóły

Począwszy od platformy .NET Core 3,0, mapowanie ustawień regionalnych "C" zostało zmienione tak, aby korzystało z niezmiennej ustawień regionalnych zamiast en_US_POSIX. Ustawienia regionalne "C" do mapowania niezmiennej są również stosowane do systemu Windows w celu zapewnienia spójności.

Mapowanie "C" na kulturę en_US_POSIX spowodowało pomyłkę klienta, ponieważ en_US_POSIX nie obsługuje operacji wyszukiwania ciągów z uwzględnieniem wielkości liter. Ponieważ ustawienia regionalne "C" są używane jako domyślne ustawienia regionalne dla niektórych dystrybucje systemu Linux, klienci napotykali to niepożądane zachowanie w tych systemach operacyjnych. 

#### <a name="version-introduced"></a>Wprowadzona wersja

.NET Core 3.0

### <a name="recommended-action"></a>Zalecana akcja

Niczego nie ma więcej niż świadomość tej zmiany. Ta zmiana dotyczy tylko aplikacji, które korzystają z mapowania ustawień regionalnych "C".

### <a name="category"></a>Kategoria

Globalizacja 

### <a name="affected-apis"></a>Dotyczy interfejsów API

Ta zmiana ma wpływ na wszystkie interfejsy API sortowania i kultury.

<!--

-->
