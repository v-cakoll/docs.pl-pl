---
title: Klasa AssemblyAttributesGoHereSM (System. Runtime. CompilerServices)
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
ms.openlocfilehash: 379ba20ebf675bec71e6e5f5bcfc0dc2fbd1f92c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446600"
---
# <a name="assemblyattributesgoheresm-class"></a>Klasa AssemblyAttributesGoHereSM

Używane przez ALink jako symbol zastępczy do przechowywania informacji o atrybutach niestandardowych.

## <a name="syntax"></a>Składnia

```csharp
internal sealed class AssemblyAttributesGoHereSM
```

## <a name="remarks"></a>Uwagi

Odwołania do tego typu mogą być osadzone w modułach, których źródła zawierają atrybuty niestandardowe zestawu. Podczas kompilowania manifestu zestawu z co najmniej jednego modułu, który zawiera odwołania do tych typów, ALink używa informacji dołączonych do tych odwołań do emisji prawdziwych atrybutów niestandardowych. W związku z tym ten typ nigdy nie jest tworzony i odwołania do niego są używane tylko jako część procesu kompilacji i nie mają zastosowania w końcowym zestawie.

Odwołania do tego typu wskazują atrybuty niestandardowe, które są związane z zabezpieczeniami i wielokrotnym użyciem.

Te typy są oznaczone jako "wewnętrzne" w .NET Framework i znajdują się w przestrzeni nazw <xref:System.Runtime.CompilerServices>.

## <a name="requirements"></a>Wymagania

mscorlib.dll

## <a name="see-also"></a>Zobacz także

- [AssemblyAttributesGoHere](assemblyattributesgohere.md)
- [AssemblyAttributesGoHereM](assemblyattributesgoherem.md)
- [AssemblyAttributesGoHereS](assemblyattributesgoheres.md)
