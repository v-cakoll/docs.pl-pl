---
title: Członkowie (F#)
description: Dowiedz się więcej o elementach członkowskich obiektu w F# języka programowania.
ms.date: 05/16/2016
ms.openlocfilehash: 6dcdb1d7fa061fb838d4aa8f7a2912fd168c3781
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "33562211"
---
# <a name="members"></a>Elementy członkowskie

W tej sekcji opisano elementy członkowskie F# typy obiektów.


## <a name="remarks"></a>Uwagi
*Elementy członkowskie* funkcje, które są częścią definicji typu i są uznane za pomocą `member` — słowo kluczowe. F#typy obiektów, takich jak rekordy, klas, rekord z wariantami, interfejsów i struktury obsługuje elementy członkowskie. Aby uzyskać więcej informacji, zobacz [rekordów](../records.md), [klasy](../classes.md), [sumy rozłączne](../discriminated-Unions.md), [interfejsów](../interfaces.md), i [struktury](../structures.md).

Elementy członkowskie zwykle tworzą interfejsu publicznego dla typu, dlatego są publiczne, chyba że określono inaczej. Prywatne lub wewnętrzne, mogą być także zadeklarowane elementy członkowskie. Aby uzyskać więcej informacji, zobacz [kontroli dostępu](../access-Control.md). Podpisy dla typów może również służyć do ujawniają i nie ujawnia niektóre elementy członkowskie typu. Aby uzyskać więcej informacji, zobacz [podpisy](../signatures.md).

Pola prywatne i `do` powiązania, które są używane tylko z klasami, nie są członkami wartość true, ponieważ nigdy nie są częścią interfejsu publicznego typu i nie są zadeklarowane za pomocą `member` — słowo kluczowe, ale są opisane w tej sekcji również.


## <a name="related-topics"></a>Tematy pokrewne


|Temat|Opis|
|-----|-----------|
|[`let` Powiązania w klasach](let-bindings-in-classes.md)|W tym artykule opisano definicji pola prywatne i funkcje w klasach.|
|[`do` Powiązania w klasach](do-bindings-in-classes.md)|W tym artykule opisano specyfikację kod inicjowania obiektu.|
|[Właściwości](properties.md)|Opisuje właściwości składowych w klasach i innych typów.|
|[Właściwości indeksowane](indexed-properties.md)|Opisuje właściwości tablicy w klasach i innych typów.|
|[Metody](methods.md)|Opisuje funkcje, które są elementami członkowskimi typu.|
|[Konstruktory](constructors.md)|W tym artykule opisano funkcje specjalne, które Inicjowanie obiektów typu.|
|[Przeładowanie operatora](../operator-overloading.md)|W tym artykule opisano definicję niestandardowych operatorów dla typów.|
|[Zdarzenia](events.md)|W tym artykule opisano definicji zdarzeń i zdarzeń w F#.|
|[Pola jawne: słowo kluczowe `val`](explicit-fields-the-val-keyword.md)|W tym artykule opisano definicji niezainicjowanej pola w typie.|
