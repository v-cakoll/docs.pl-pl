---
title: Członkowie (F#)
description: 'Informacje o elementach członkowskich obiektu w języku programowania w języku F #.'
keywords: 'Visual f #, f #, funkcjonalności programowania'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e472f50a-4939-4e62-abbc-471f8f265790
ms.openlocfilehash: ca34c8d073594791ec268a85ad56f50cc6d9e435
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="members"></a>Elementy członkowskie

W tej sekcji opisano elementy członkowskie typów obiektów języka F #.


## <a name="remarks"></a>Uwagi
*Elementy członkowskie* są funkcje, które są częścią definicji typu i został zadeklarowany z `member` — słowo kluczowe. Suma rozłączna — obiekt typów F # takich jak rekordy, klasy, Unii, interfejsów, i struktury obsługi elementów członkowskich. Aby uzyskać więcej informacji, zobacz [rekordów](../records.md), [klasy](../classes.md), [Suma rozłączna unie](../discriminated-Unions.md), [interfejsów](../interfaces.md), i [struktury](../structures.md).

Elementy członkowskie zwykle składają się interfejsu publicznego dla typu, dlatego są one publiczne, chyba że określono inaczej. Elementy Członkowskie mogą być deklarowane również w prywatny lub wewnętrzny. Aby uzyskać więcej informacji, zobacz [kontroli dostępu](../access-Control.md). Podpisy dla typów może również służyć do ujawniają i nie ujawnia niektóre elementy członkowskie typu. Aby uzyskać więcej informacji, zobacz [podpisy](../signatures.md).

Pól prywatnych i `do` powiązania, które są używane tylko z klasami, nie są członkami wartość true, ponieważ nigdy nie są częścią interfejsu publicznego typu i nie został zadeklarowany z `member` — słowo kluczowe, ale są opisane w tej sekcji również.


## <a name="related-topics"></a>Tematy pokrewne


|Temat|Opis|
|-----|-----------|
|[`let`Powiązania w klasach](let-bindings-in-classes.md)|Zawiera opis definicji pól prywatnych i funkcje w klasach.|
|[`do`Powiązania w klasach](do-bindings-in-classes.md)|W tym artykule opisano specyfikację kod inicjujący obiektu.|
|[Właściwości](properties.md)|Opisuje właściwości członków klasy i innych typów.|
|[Właściwości indeksowane](indexed-properties.md)|Opisuje właściwości tablicy w klasami i innymi typami.|
|[Metody](methods.md)|W tym artykule opisano funkcje, które są elementami członkowskimi typu.|
|[Konstruktory](constructors.md)|Opisuje specjalne funkcje, które Inicjowanie obiektów typu.|
|[Przeładowanie operatora](../operator-overloading.md)|Zawiera opis definicji operatorów niestandardowe dla typów.|
|[Zdarzenia](events.md)|Zawiera opis definicji zdarzenia i zdarzeń w języku F #.|
|[Pola jawne: `val` — słowo kluczowe](explicit-fields-the-val-keyword.md)|Zawiera opis definicji niezainicjowanej pól w typie.|
