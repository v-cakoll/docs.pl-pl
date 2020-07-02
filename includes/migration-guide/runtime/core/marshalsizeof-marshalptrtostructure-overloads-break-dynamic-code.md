---
ms.openlocfilehash: c462c7b4ec8423ce8fd331d3cd31154283cf1f1d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620258"
---
### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a>Marshal. SizeOf i Marshaling. PtrToStructure overloads Break Dynamic Code

#### <a name="details"></a>Szczegóły

Począwszy od .NET Framework 4.5.1, dynamiczne powiązanie z metodami,,,, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601> <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)> <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)> <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)> <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)> lub <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)> , (za pomocą programu Windows PowerShell, IronPython lub dynamicznego słowa kluczowego C#, na przykład) może spowodować, <code>MethodInvocationExceptions</code> że dodano nowe przeciążenia tych metod, które mogą być niejednoznaczne dla aparatów obsługi skryptów.

#### <a name="suggestion"></a>Sugestia

Aktualizuj skrypty, aby jasno wskazać, które Przeciążenie powinno być używane. Można to zrobić zazwyczaj przez jawne rzutowanie parametrów typu metody na <xref:System.Type> . Zobacz [ten link](https://support.microsoft.com/kb/2909958/) , aby uzyskać szczegółowe informacje i przykłady obejścia problemu.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|
