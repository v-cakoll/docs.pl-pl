---
title: Klasa AssemblyAttributesGoHereM (System. Runtime. CompilerServices)
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereM
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereM
helpviewer_keywords:
- AssemblyAttributesGoHereM type
- Alink API, AssemblyAttributesGoHereM type
ms.assetid: caaa8ba9-b4bb-4dd6-934d-57e436b2f3e5
topic_type:
- apiref
ms.openlocfilehash: 15b9445aa3eabbd14541cfe5481bfb553c8c0347
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446631"
---
# <a name="assemblyattributesgoherem-class"></a>Klasa AssemblyAttributesGoHereM

Używane przez ALink jako symbol zastępczy do przechowywania informacji o atrybutach niestandardowych.

## <a name="syntax"></a>Składnia

```csharp
internal sealed class AssemblyAttributesGoHereM
```

## <a name="remarks"></a>Uwagi

Odwołania do tego typu mogą być osadzone w modułach, których źródła zawierają atrybuty niestandardowe zestawu. Podczas kompilowania manifestu zestawu z co najmniej jednego modułu, który zawiera odwołania do tych typów, ALink używa informacji dołączonych do tych odwołań do emisji prawdziwych atrybutów niestandardowych. W związku z tym ten typ nigdy nie jest tworzony i odwołania do niego są używane tylko jako część procesu kompilacji i nie mają zastosowania w końcowym zestawie.

Odwołania do tego typu wskazują atrybuty niestandardowe, które nie są powiązane z zabezpieczeniami, ale są wielokrotnością użycia.

Te typy są oznaczone jako "wewnętrzne" w .NET Framework i znajdują się w przestrzeni nazw <xref:System.Runtime.CompilerServices>.

## <a name="requirements"></a>Wymagania

mscorlib.dll

## <a name="see-also"></a>Zobacz także

- [AssemblyAttributesGoHere](assemblyattributesgohere.md)
- [AssemblyAttributesGoHereS](assemblyattributesgoheres.md)
- [AssemblyAttributesGoHereSM](assemblyattributesgoheresm.md)
