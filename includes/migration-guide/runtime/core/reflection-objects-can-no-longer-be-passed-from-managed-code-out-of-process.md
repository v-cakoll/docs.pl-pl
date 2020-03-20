---
ms.openlocfilehash: 38c774417fc94fa080bf2b82c04d575e9068cdcb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858832"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a>Nie można już przepuszczać obiektów odbicia z kodu zarządzanego do pozatemaowych klientów DCOM

|   |   |
|---|---|
|Szczegóły|Odbicie obiekty nie mogą być już przekazywane z kodu zarządzanego do klientów DCOM poza procesem. Dotyczy to następujących typów:<ul><li><xref:System.Reflection.Assembly?displayProperty=name></li><li><xref:System.Reflection.MemberInfo?displayProperty=name>(i jego typy <xref:System.Reflection.FieldInfo?displayProperty=name>pochodne, w tym <xref:System.Reflection.MethodInfo?displayProperty=name>, , <xref:System.Type?displayProperty=name>i <xref:System.Reflection.TypeInfo?displayProperty=name>)</li><li><xref:System.Reflection.MethodBody?displayProperty=name></li><li><xref:System.Reflection.Module?displayProperty=name></li><li><xref:System.Reflection.ParameterInfo?displayProperty=name>.</li></ul>Wywołania <code>IMarshal</code> zwracania <code>E_NOINTERFACE</code>obiektu .|
|Sugestia|Aktualizowanie kodu organizowania w celu pracy z obiektami nierefleksji|
|Zakres|Mały|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|
