---
title: 1004 — WorkflowInstanceAborted
ms.date: 03/30/2017
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
ms.openlocfilehash: d34f6f1ab6af8e06a0f28fb043faf9fe16a8b211
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485190"
---
# <a name="1004---workflowinstanceaborted"></a>1004 — WorkflowInstanceAborted

## <a name="properties"></a>Właściwości

|||
|-|-|
|ID|1004|
|Słowa kluczowe|WFRuntime|
|Poziom|Informacje|
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|

## <a name="description"></a>Opis

Wskazuje, że wystąpienie przepływu pracy, została przerwana z powodu wyjątku.

## <a name="message"></a>Komunikat

WorkflowInstance Id: "%1" została przerwana z powodu wyjątku.

## <a name="details"></a>Szczegóły

|Nazwa elementu danych|Typ elementu danych|Opis|
|--------------------|--------------------|-----------------|
|WorkflowInstanceId|`xs:string`|Identyfikator wystąpienia przepływu pracy|
|Wyjątek|`xs:string`|Szczegóły wyjątku, dla wyjątku|
|AppDomain|`xs:string`|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
