---
title: Obsługa platformy .NET Core
description: Dowiedz się więcej o obsługuje train inną wersję (LTS i bieżący) dla platformy .NET Core
author: kendrahavens
ms.author: mairaw
ms.date: 01/30/2017
ms.openlocfilehash: b61aa48451cee60be4968c151b97746a3aef85c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="net-core-support"></a>Obsługa platformy .NET Core

Jest to ogólny opis pomocy technicznej platformy .NET Core.

## <a name="lts-and-current-release-trains"></a>LTS i bieżącego pociągu zlecenia

Dwa pociągu wersji pomocy technicznej jest wspólne pojęcia używane na świecie oprogramowania specjalnie dla projektów open source, takich jak .NET Core. .NET core obsługę następujących wersji pociągu: [długi okres obsługuje (LTS)](https://en.wikipedia.org/wiki/Long-term_support) i aktualne. LTS wersje są obsługiwane dla stabilności przez cały cykl ich życia odbieranie poprawki dotyczące ważnych problemów i poprawki zabezpieczeń. Nowej pracy funkcji oraz poprawek dodatkowe miejsce w bieżącej wersji. Z punktu widzenia obsługi te wersji pociągu mają poniższe obsługuje atrybutów cyklu życia.

Są wersje LTS
* Obsługiwane przez 3 lata po dacie ogólnodostępnej wersji LTS
* Lub co rok po udostępnieniu wersji ogólnodostępnej kolejnych wersji LTS

Bieżące wersje są
* Obsługiwane w tym samym oknie trzech lat jako zlecenia LTS nadrzędnego
* Obsługiwane przez trzy miesiące po udostępnieniu wersji ogólnodostępnej kolejnych bieżącej wersji
* I jeden rok po udostępnieniu wersji ogólnodostępnej kolejnych wersji LTS

## <a name="versioning"></a>Przechowywanie wersji
Nowości LTS są oznaczane przez zwiększenie numeru wersji głównej. Bieżące wersje mają ten sam numer głównych jako odpowiednie train LTS i oznaczonych przez zwiększenie numeru wersji pomocniczej. Na przykład 1.0.3 byłoby LTS i 1.1.0 będzie bieżącej. Poprawka błędu albo przyrost train aktualizacji wersji poprawki. Aby uzyskać więcej informacji na schemat przechowywania wersji, zobacz [.NET Core Versioning](index.md).

## <a name="what-causes-updates-in-lts-and-current-trains"></a>Aktualizacje co powoduje LTS i bieżącego pociągu?
Aby zrozumieć, jakie określone zmiany, takie jak poprawki lub dodanie interfejsów API, powodują aktualizacji do wersji numery zapoznaj się z sekcją drzewa decyzyjnego w [dokumentacji Versioning](index.md). Złotego zestaw reguł, które zdecyduj, jakie zmiany są pobierane do bieżącej gałęzi LTS nie istnieje. Zazwyczaj zabezpieczeń niezbędne aktualizacje i poprawki, które napraw oczekiwanego zachowania są powodów można zaktualizować gałęzi LTS. Firma Microsoft również zamierzasz obsługuje najnowsze systemy operacyjne projektanta pulpitu w gałęzi LTS, chociaż to może nie zawsze jest możliwe. Jest to dobry sposób na nadążyć na jakie interfejsów API, poprawki i systemy operacyjne są obsługiwane w niektórych wersji do przeglądania jego [informacje o wersji](https://github.com/dotnet/core/tree/master/release-notes) w witrynie GitHub.

### <a name="further-reading"></a>Dalsze informacje
* [.NET core pomocy technicznej cyklu życia faktu arkusza](https://www.microsoft.com/net/core/support)
* [Obecnie obsługiwane systemy operacyjne i wersje](https://github.com/dotnet/core/blob/master/roadmap.md)
