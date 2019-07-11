---
title: AssemblyAttributesGoHereS
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereS
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereS
helpviewer_keywords:
- AssemblyAttributesGoHereS type
- Alink API, AssemblyAttributesGoHereS type
ms.assetid: 4e817f35-a2bc-4403-9e6f-f731e6b9fe23
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 135938c4ed91423145ca46b743620f4236f7f818
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742256"
---
# <a name="assemblyattributesgoheres"></a>AssemblyAttributesGoHereS

Używane przez ALink, jako symbol zastępczy do przechowywania informacji na temat atrybutów niestandardowych.

## <a name="syntax"></a>Składnia

```csharp
internal sealed class AssemblyAttributesGoHereS
```

## <a name="remarks"></a>Uwagi

Odwołania do tego typu może być osadzony wewnątrz modułów sieciowych, których źródła zawierają zestaw atrybutów niestandardowych. Podczas tworzenia manifestu zestawu z jednego lub więcej modułów sieciowych, które zawierają odwołania do tych typów, ALink używa informacji o dołączonych do tych odwołań do emitowania rzeczywiste niestandardowych atrybutów. W efekcie tego typu nigdy nie zostanie uruchomiony, a odwołania do niego są używane tylko jako część procesu kompilacji i spełniać nie zadania w końcowym zestawie.

Odwołania do tego typu wskazują atrybutów niestandardowych, które są związane z zabezpieczeniami i nie są wielokrotnego użytku.

Te typy są oznaczone jako "internal" w ramach programu .NET Framework i znajdują się w <xref:System.Runtime.CompilerServices> przestrzeni nazw.

## <a name="requirements"></a>Wymagania

mscorlib.dll

## <a name="see-also"></a>Zobacz także

- [AssemblyAttributesGoHere](assemblyattributesgohere.md)
- [AssemblyAttributesGoHereM](assemblyattributesgoherem.md)
- [AssemblyAttributesGoHereSM](assemblyattributesgoheresm.md)
