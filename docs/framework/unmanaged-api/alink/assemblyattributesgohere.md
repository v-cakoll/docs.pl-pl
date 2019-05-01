---
title: Assemblyattributesgohere — klasa (System.Runtime.CompilerServices)
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHere
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHere
helpviewer_keywords:
- AssemblyAttributesGoHere type
- Alink API, AssemblyAttributesGoHere type
ms.assetid: 7b26fcb6-94f4-4f09-933e-b33efe451f4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 571c2f6723e827a1b385f77724c33703ae970ae3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775625"
---
# <a name="assemblyattributesgohere-class"></a>Assemblyattributesgohere — klasa

Używane przez ALink, jako symbol zastępczy do przechowywania informacji na temat atrybutów niestandardowych.

## <a name="syntax"></a>Składnia

```csharp
internal sealed class AssemblyAttributesGoHere
```

## <a name="remarks"></a>Uwagi

Odwołania do tego typu może być osadzony wewnątrz modułów sieciowych, których źródła zawierają zestaw atrybutów niestandardowych. Podczas tworzenia manifestu zestawu z jednego lub więcej modułów sieciowych, które zawierają odwołania do tych typów, ALink używa informacji o dołączonych do tych odwołań do emitowania rzeczywiste niestandardowych atrybutów. W efekcie tego typu nigdy nie zostanie uruchomiony, a odwołania do niego są używane tylko jako część procesu kompilacji i spełniać nie zadania w końcowym zestawie.

Odwołania do tego typu wskazują atrybutów niestandardowych, które nie są związane z zabezpieczeniami i nie są wielokrotnego użytku.

Te typy są oznaczone jako "internal" w ramach programu .NET Framework i znajdują się w <xref:System.Runtime.CompilerServices> przestrzeni nazw.

## <a name="requirements"></a>Wymagania

mscorlib.dll

## <a name="see-also"></a>Zobacz także

- [AssemblyAttributesGoHereM](assemblyattributesgoherem.md)
- [AssemblyAttributesGoHereS](assemblyattributesgoheres.md)
- [AssemblyAttributesGoHereSM](assemblyattributesgoheresm.md)
