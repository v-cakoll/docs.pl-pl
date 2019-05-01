---
title: Assemblyattributesgoheresm — klasa (System.Runtime.CompilerServices)
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereSM
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereSM
helpviewer_keywords:
- AssemblyAttributesGoHereSM type
- Alink API, AssemblyAttributesGoHereSM type
ms.assetid: 4cf9bf39-1527-49e0-a0e9-55e7a018bf66
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 01b156ed9c318e71a408ea10f2744911a85faedc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790341"
---
# <a name="assemblyattributesgoheresm-class"></a>Assemblyattributesgoheresm — klasa

Używane przez ALink, jako symbol zastępczy do przechowywania informacji na temat atrybutów niestandardowych.

## <a name="syntax"></a>Składnia

```csharp
internal sealed class AssemblyAttributesGoHereSM
```

## <a name="remarks"></a>Uwagi

Odwołania do tego typu może być osadzony wewnątrz modułów sieciowych, których źródła zawierają zestaw atrybutów niestandardowych. Podczas tworzenia manifestu zestawu z jednego lub więcej modułów sieciowych, które zawierają odwołania do tych typów, ALink używa informacji o dołączonych do tych odwołań do emitowania rzeczywiste niestandardowych atrybutów. W efekcie tego typu nigdy nie zostanie uruchomiony, a odwołania do niego są używane tylko jako część procesu kompilacji i spełniać nie zadania w końcowym zestawie.

Odwołania do tego typu wskazują atrybutów niestandardowych, które są powiązane i wielokrotnego użytku zabezpieczeń.

Te typy są oznaczone jako "internal" w ramach programu .NET Framework i znajdują się w <xref:System.Runtime.CompilerServices> przestrzeni nazw.

## <a name="requirements"></a>Wymagania

mscorlib.dll

## <a name="see-also"></a>Zobacz także

- [AssemblyAttributesGoHere](assemblyattributesgohere.md)
- [AssemblyAttributesGoHereM](assemblyattributesgoherem.md)
- [AssemblyAttributesGoHereS](assemblyattributesgoheres.md)
