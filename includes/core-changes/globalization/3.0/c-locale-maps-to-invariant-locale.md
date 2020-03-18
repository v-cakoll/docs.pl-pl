---
ms.openlocfilehash: d35de48dd22003c851cf5dba9e8517ec48b9217b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567782"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a>Mapy regionalne "C" do niezmiennych ustawień regionalnych

.NET Core 2.2 i wcześniejsze wersje zależą od domyślnego zachowania ICU, które mapuje ustawienia regionalne "C" na ustawienia regionalne en_US_POSIX. Ustawienia regionalne en_US_POSIX ma niepożądane zachowanie sortowania, ponieważ nie obsługuje porównania ciągów bez uwzględniania wielkości liter. Ponieważ niektóre dystrybucje systemu Linux ustawić ustawienia regionalne "C" jako domyślne ustawienia regionalne, użytkownicy doświadczali nieoczekiwane zachowanie.

#### <a name="change-description"></a>Zmień opis

Począwszy od .NET Core 3.0, mapowanie ustawień regionalnych "C" zostało zmienione, aby użyć ustawień regionalnych Niezmienne zamiast en_US_POSIX. Ustawienia regionalne "C" do mapowania niezmiennego jest również stosowany do systemu Windows dla spójności.

Mapowanie "C" na kulturę en_US_POSIX spowodowało zamieszanie klientów, ponieważ en_US_POSIX nie obsługuje operacji sortowania/wyszukiwania ciągów bez uwzględniania wielkości liter. Ponieważ ustawienia regionalne "C" są używane jako domyślne ustawienia regionalne w niektórych dystrybucjach systemu Linux, klienci doświadczyli tego niepożądanego zachowania w tych systemach operacyjnych.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

### <a name="recommended-action"></a>Zalecana akcja

Nic konkretnego więcej niż świadomość tej zmiany. Ta zmiana dotyczy tylko aplikacji, które używają mapowania ustawień regionalnych "C".

### <a name="category"></a>Kategoria

Globalizacja

### <a name="affected-apis"></a>Dotyczy interfejsów API

Ta zmiana dotyczy wszystkich interfejsów API sortowania i kultury.

<!--

-->
