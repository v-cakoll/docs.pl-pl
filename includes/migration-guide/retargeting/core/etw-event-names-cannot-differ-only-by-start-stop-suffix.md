---
ms.openlocfilehash: 0e25d5d9b545e5cb400cbf701fb13da572fadf10
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614675"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a>Nazwy zdarzeń ETW nie mogą się różnić tylko sufiksem "Start" lub "Stop"

#### <a name="details"></a>Szczegóły

W .NET Framework 4,6 i 4.6.1 środowisko uruchomieniowe zgłasza, <xref:System.ArgumentException> kiedy dwa zdarzenia śledzenia zdarzeń dla systemu Windows (ETW) różnią się tylko sufiksem "Start" lub "Zatrzymaj" (tak, jakby jedno zdarzenie o nazwie zostało nazwane `LogUser` i ma nazwę `LogUserStart` ). W tym przypadku środowisko uruchomieniowe nie może skonstruować źródła zdarzeń, co nie może emitować żadnego rejestrowania.

#### <a name="suggestion"></a>Sugestia

Aby zapobiec wyjątku, należy się upewnić, że żadne dwa nazwy zdarzeń nie różnią się tylko sufiksem "Start" lub "Stop". Ten wymóg jest usuwany, rozpoczynając od .NET Framework 4.6.2; środowisko uruchomieniowe może odróżnić nazwy zdarzeń, które różnią się tylko sufiksem "Start" i "Stop".

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4.6         |
| Typ    | Przekierowanie |
