---
title: Zdarzenia ETW dotyczące rywalizacji — .NET
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
ms.openlocfilehash: 98fc2adcaebe4c9646ab9960f796982681a9015a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716134"
---
# <a name="contention-etw-events"></a>Zdarzenia ETW dotyczące rywalizacji

Zdarzenia rywalizacji są wywoływane zawsze wtedy, gdy istnieje rywalizacja o <xref:System.Threading.Monitor?displayProperty=nameWithType> blokad lub blokad natywnych używanych przez środowisko uruchomieniowe. Rywalizacja występuje, gdy wątek oczekuje na blokadę, a inny wątek posiada blokadę.

W poniższej tabeli przedstawiono słowo kluczowe, pod którym są wywoływane zdarzenia rywalizacji, oraz poziom zdarzeń. Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md).

|Słowo kluczowe do podniesienia zdarzenia|Poziom|
|-----------------------------------|-----------|
|`ContentionKeyword` (0x4000)|Informacyjny (4)|

W poniższej tabeli przedstawiono informacje o zdarzeniach:

|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|81|Rozpocznie się rywalizację. To zdarzenie nie obejmuje ilości czasu nawirowania, zanim wątek czeka na uzyskanie blokady; jest uruchamiany tylko wtedy, gdy wątek czeka na uzyskanie blokady.|
|`ContentionStop`|91|Zakończyło się rywalizację.|

W poniższej tabeli przedstawiono dane zdarzenia:

|Nazwa pola|Typ danych|Opis|
|----------------|---------------|-----------------|
|Flagi|win: UInt8|0 dla zarządzanych; 1 w przypadku kodu natywnego.|
|ClrInstanceID|Win: UInt16|Unikatowy identyfikator wystąpienia środowiska CLR.|

## <a name="see-also"></a>Zobacz także

- [Zdarzenia CLR ETW](clr-etw-events.md)
