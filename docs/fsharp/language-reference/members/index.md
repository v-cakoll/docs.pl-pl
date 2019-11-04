---
title: Elementy członkowskie
description: Dowiedz się więcej o elementach członkowskich obiektów w języku F# programowania.
ms.date: 05/16/2016
ms.openlocfilehash: 2e85d014cd1e9b7997638cb210fed5705c217719
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425071"
---
# <a name="members"></a>Elementy członkowskie

W F# tej sekcji opisano elementy członkowskie typów obiektów.

## <a name="remarks"></a>Uwagi

*Elementy członkowskie* są funkcjami, które są częścią definicji typu i są zadeklarowane za pomocą słowa kluczowego `member`. F#typy obiektów, takie jak rekordy, klasy, Unii rozłącznych, interfejsy i struktury, obsługują członków. Aby uzyskać więcej informacji, zobacz [rekordy](../records.md), [klasy](../classes.md), [związki rozłącznych](../discriminated-Unions.md), [interfejsy](../interfaces.md)i [struktury](../structures.md).

Członkowie zwykle tworzą interfejs publiczny dla typu, dlatego są one publiczne, chyba że określono inaczej. Elementy członkowskie mogą być również deklarowane jako prywatne lub wewnętrzne. Aby uzyskać więcej informacji, zobacz [Access Control](../access-Control.md). Sygnatury typów mogą być również używane do ujawniania lub nieujawniania określonych elementów członkowskich typu. Aby uzyskać więcej informacji, zobacz [podpisy](../signature-files.md).

Pola prywatne i powiązania `do`, które są używane tylko z klasami, nie są prawdziwymi elementami członkowskimi, ponieważ nigdy nie są częścią publicznego interfejsu typu i nie są zadeklarowane za pomocą słowa kluczowego `member`, ale są opisane w tej sekcji.

## <a name="related-topics"></a>Tematy pokrewne

|Temat|Opis|
|-----|-----------|
|[`let` powiązania w klasach](let-bindings-in-classes.md)|Opisuje definicje pól i funkcji prywatnych w klasach.|
|[`do` powiązania w klasach](do-bindings-in-classes.md)|Opisuje specyfikację kodu inicjalizacji obiektu.|
|[Właściwości](properties.md)|Opisuje elementy członkowskie właściwości w klasach i innych typach.|
|[Właściwości indeksowane](indexed-properties.md)|Opisuje właściwości podobne do tablic w klasach i innych typach.|
|[Metody](methods.md)|Opisuje funkcje, które są elementami członkowskimi typu.|
|[Konstruktory](constructors.md)|Opisuje funkcje specjalne, które inicjują obiekty typu.|
|[Przeładowanie operatora](../operator-overloading.md)|Opisuje definicje niestandardowych operatorów dla typów.|
|[Zdarzenia](events.md)|Opisuje definicje zdarzeń i obsługi zdarzeń w programie F#.|
|[Pola jawne: słowo kluczowe `val`](explicit-fields-the-val-keyword.md)|Opisuje definicje niezainicjowanych pól w typie.|
