---
ms.openlocfilehash: a54b17b2002bd0f85b8b47c5e37e040470d6c494
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621334"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a>Obiektów odbicia nie można już przekazywać z kodu zarządzanego do pozaprocesowych klientów DCOM.

#### <a name="details"></a>Szczegóły

Obiektów odbicia nie można już przekazywać z kodu zarządzanego do pozaprocesowych klientów DCOM. Dotyczy to następujących typów:<ul><li><xref:System.Reflection.Assembly?displayProperty=fullName></li><li><xref:System.Reflection.MemberInfo?displayProperty=fullName>(i jego typy pochodne, w tym <xref:System.Reflection.FieldInfo?displayProperty=fullName> , <xref:System.Reflection.MethodInfo?displayProperty=fullName> , <xref:System.Type?displayProperty=fullName> i <xref:System.Reflection.TypeInfo?displayProperty=fullName> )</li><li><xref:System.Reflection.MethodBody?displayProperty=fullName></li><li><xref:System.Reflection.Module?displayProperty=fullName></li><li><xref:System.Reflection.ParameterInfo?displayProperty=fullName>.</li></ul>Wywołania do <code>IMarshal</code> zwracanego obiektu <code>E_NOINTERFACE</code> .

#### <a name="suggestion"></a>Sugestia

Aktualizuj kod kierujący do pracy z obiektami nieodbicia

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|
