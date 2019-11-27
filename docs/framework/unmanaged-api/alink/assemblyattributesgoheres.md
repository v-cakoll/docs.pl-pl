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
ms.openlocfilehash: 128268bab77c8be5dc809eaa6d2548fc34f13cbd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446621"
---
# <a name="assemblyattributesgoheres"></a>AssemblyAttributesGoHereS

Używane przez ALink jako symbol zastępczy do przechowywania informacji o atrybutach niestandardowych.

## <a name="syntax"></a>Składnia

```csharp
internal sealed class AssemblyAttributesGoHereS
```

## <a name="remarks"></a>Uwagi

Odwołania do tego typu mogą być osadzone w modułach, których źródła zawierają atrybuty niestandardowe zestawu. Podczas kompilowania manifestu zestawu z co najmniej jednego modułu, który zawiera odwołania do tych typów, ALink używa informacji dołączonych do tych odwołań do emisji prawdziwych atrybutów niestandardowych. W związku z tym ten typ nigdy nie jest tworzony i odwołania do niego są używane tylko jako część procesu kompilacji i nie mają zastosowania w końcowym zestawie.

Odwołania do tego typu wskazują atrybuty niestandardowe, które są powiązane z zabezpieczeniami i nie są wielokrotnością użycia.

Te typy są oznaczone jako "wewnętrzne" w .NET Framework i znajdują się w przestrzeni nazw <xref:System.Runtime.CompilerServices>.

## <a name="requirements"></a>Wymagania

mscorlib.dll

## <a name="see-also"></a>Zobacz także

- [AssemblyAttributesGoHere](assemblyattributesgohere.md)
- [AssemblyAttributesGoHereM](assemblyattributesgoherem.md)
- [AssemblyAttributesGoHereSM](assemblyattributesgoheresm.md)
