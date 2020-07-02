---
ms.openlocfilehash: 0bd90b3d479a7e0897aaf78b7718ae156a4a239f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620194"
---
### <a name="assemblies-compiled-with-regexcompiletoassembly-breaks-between-40-and-45"></a>Zestawy skompilowane z wyrażeniem regularnym. CompileToAssembly są rozdzielonymi między 4,0 i 4,5

#### <a name="details"></a>Szczegóły

Jeśli zestaw skompilowanych wyrażeń regularnych jest skompilowany przy użyciu .NET Framework 4,5, ale jest przeznaczony dla .NET Framework 4, próba użycia jednego z wyrażeń regularnych w tym zestawie w systemie z zainstalowanym programem .NET Framework 4 zgłasza wyjątek.

#### <a name="suggestion"></a>Sugestia

Aby obejść ten problem, można wykonać jedną z następujących czynności:<ul><li>Kompiluj zestaw zawierający wyrażenia regularne z .NET Framework 4.</li><li>Użyj interpretowanego wyrażenia regularnego.</li></ul>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName)?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[])?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[],System.String)?displayProperty=nameWithType></li></ul>|
