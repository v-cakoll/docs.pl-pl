---
title: -Nullable (opcje kompilatora C#)
ms.date: 06/04/2020
f1_keywords:
- /nullable
helpviewer_keywords:
- nullable compiler option [C#]
- /nullable compiler option [C#]
- -nullable compiler option [C#]
ms.openlocfilehash: a68255dba18a022784cd4aaf0027c371893c577b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2020
ms.locfileid: "84449814"
---
# <a name="-nullable-c-compiler-options"></a>-Nullable (opcje kompilatora C#)

Opcja **-nullable** pozwala określić żądany kontekst dopuszczający wartość null.

## <a name="syntax"></a>Składnia

```console
-nullable[+ | -]
-nullable:{enable | disable | warnings | annotations}
```

## <a name="arguments"></a>Argumenty

`+`&#124;`-`  
Określanie `+` lub **dopuszczanie wartości null**powoduje, że kompilator włącza kontekst dopuszczający wartości null. Określenie `-` , która obowiązuje, jeśli nie określono **wartości null**, wyłącza kontekst dopuszczający wartości null.

`enable`&#124; `disable` &#124; `warnings` &#124;`annotations`  
Określa opcję kontekstową dopuszczającą wartość null. Podobnie jak w przypadku programu `+` lub `-` , aby włączyć i wyłączyć, ale pozwala na zwiększenie stopnia szczegółowości dla specyficznych dla kontekstu wartości null. `enable`Argument, który działa tak samo jak w przypadku określenia **wartości null**, włącza kontekst dopuszczający wartość null. Określenie `disable` spowoduje wyłączenie kontekstu dopuszczającego wartość null. Gdy podajesz `warnings` argument, **-nullable:** Warnings, jest włączony kontekst ostrzeżenia dopuszczający wartość null. Podczas określania `annotations` argumentu **-nullable: adnotacje**kontekst adnotacji z dopuszczaniem wartości null jest włączony.

## <a name="remarks"></a>Uwagi

Analiza przepływu służy do wywnioskowania wartości null zmiennych w kodzie wykonywalnym. Wywnioskowana wartość null zmiennej jest niezależna od zadeklarowanej wartości null zmiennej. Wywołania metod są analizowane nawet wtedy, gdy są warunkowo pominięte. Na przykład <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> w trybie wydania.

Wywołanie metod o następujących atrybutach będzie miało wpływ na analizę przepływu:

- Proste warunki wstępne: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> i<xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute>
- Proste warunki Post: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> i<xref:System.Diagnostics.CodeAnalysis.NotNullAttribute>
- Warunkowe warunki końcowe: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> i<xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute>
- <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute>(np. `DoesNotReturnIf(false)` dla <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ) i<xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- Warunki końcowe elementu członkowskiego: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> i<xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])>

### <a name="to-set-this-compiler-option-in-a-project"></a>Aby ustawić tę opcję kompilatora w projekcie

Edytuj element *. csproj* , aby dodać `<Nullable>` tag w `Project/PropertyGroup` hierarchii:

```xml
<Project Sdk="...">

  <PropertyGroup>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Typy referencyjne dopuszczające wartość null](../../nullable-references.md)
