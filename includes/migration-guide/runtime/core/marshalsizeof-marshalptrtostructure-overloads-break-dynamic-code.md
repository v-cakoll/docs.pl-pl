---
ms.openlocfilehash: 6309cead46dff44ff6360bac9b31666f875be210
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649311"
---
### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a>Marshal.SizeOf i przeciążenia Marshal.PtrToStructure Przerwij kod dynamicznych

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.5.1, dynamicznie powiązanie z metodami <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)>, lub <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)>, (za pośrednictwem programu Windows PowerShell, IronPython, lub C# dynamiczne słowo kluczowe, aby uzyskać np.) może spowodować <code>MethodInvocationExceptions</code> ponieważ dodano nowe przeciążenia metody te, które mogą być niejednoznaczne do aparatów obsługi skryptów.|
|Sugestia|Zaktualizuj skrypty, aby wyraźnie wskazać przeciążenie, które powinny być używane. Może to zazwyczaj wykonywane przez jawne rzutowanie parametrów typu metody jako <xref:System.Type>. Zobacz [ten link](https://support.microsoft.com/kb/2909958/) uzyskać bardziej szczegółowe informacje i przykłady sposobów w celu obejścia tego problemu.|
|Zakres|Mały|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|
