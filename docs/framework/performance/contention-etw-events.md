---
title: Zdarzenia ETW dotyczące rywalizacji — .NET
description: Uzyskaj szczegółowe informacje o zdarzeniach ETW, które są wywoływane za każdym razem, gdy istnieje rywalizacja dla elementu System. Threading. monitoruje blokady lub blokady natywne używane przez środowisko uruchomieniowe.
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
ms.openlocfilehash: a36b091e0896562fffdb66e895d70049ce0667d7
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309602"
---
# <a name="contention-etw-events"></a>Zdarzenia ETW dotyczące rywalizacji

Zdarzenia rywalizacji są wywoływane zawsze wtedy, gdy istnieje rywalizacja o <xref:System.Threading.Monitor?displayProperty=nameWithType> blokady lub blokady natywne używane przez środowisko uruchomieniowe. Rywalizacja występuje, gdy wątek oczekuje na blokadę, a inny wątek posiada blokadę.

W poniższej tabeli przedstawiono słowo kluczowe, pod którym są wywoływane zdarzenia rywalizacji, oraz poziom zdarzeń. Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md).

|Słowo kluczowe do podniesienia zdarzenia|Poziom|
|-----------------------------------|-----------|
|`ContentionKeyword`0x4000|Informacyjny (4)|

W poniższej tabeli przedstawiono informacje o zdarzeniach:

|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|81|Rozpocznie się rywalizację. To zdarzenie nie obejmuje ilości czasu nawirowania, zanim wątek czeka na uzyskanie blokady; jest uruchamiany tylko wtedy, gdy wątek czeka na uzyskanie blokady.|
|`ContentionStop`|91|Zakończyło się rywalizację.|

W poniższej tabeli przedstawiono dane zdarzenia:

|Nazwa pola|Typ danych|Opis|
|----------------|---------------|-----------------|
|Flagi|win: UInt8|0 dla zarządzanych; 1 w przypadku kodu natywnego.|
|ClrInstanceID|win: UInt16|Unikatowy identyfikator wystąpienia środowiska CLR.|

## <a name="see-also"></a>Zobacz też

- [Zdarzenia ETW CLR](clr-etw-events.md)
