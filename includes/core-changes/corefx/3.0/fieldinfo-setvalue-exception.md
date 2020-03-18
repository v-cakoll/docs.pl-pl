---
ms.openlocfilehash: dc733ee32184db5af59bb06e294cd73765977581
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449566"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a>FieldInfo.SetValue zgłasza wyjątek dla pól statycznych, tylko do init

Począwszy od .NET Core 3.0, wyjątek jest generowany podczas próby ustawienie wartości na statyczne pole, <xref:System.Reflection.FieldAttributes.InitOnly> wywołując <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.

#### <a name="change-description"></a>Zmień opis

W platformie .NET Framework i wersjach programu .NET Core przed wersją 3.0 można ustawić wartość stałego pola statycznego <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>po jego zainicjowaniu[(tylko do odczytu w języku C#),](~/docs/csharp/language-reference/keywords/readonly.md)wywołując . Jednak ustawienie takiego pola w ten sposób spowodowało nieprzewidywalne zachowanie na podstawie docelowej struktury i ustawień optymalizacji.

W wersji .NET Core 3.0 i <xref:System.Reflection.FieldInfo.SetValue%2A> nowszych, podczas <xref:System.FieldAccessException?displayProperty=nameWithType> wywoływania statycznego pola, <xref:System.Reflection.FieldAttributes.InitOnly> wyjątek.

> [!TIP]
> Pole <xref:System.Reflection.FieldAttributes.InitOnly> to pole, które można ustawić tylko w momencie, gdy jest zadeklarowany lub w konstruktorze dla klasy zawierającej. Innymi słowy, jest stała po jego zainicjowaniu.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Inicjuj <xref:System.Reflection.FieldAttributes.InitOnly> statyczne pola w konstruktorze statycznym. Dotyczy to zarówno typów dynamicznych, jak i niedynamicznych.

Alternatywnie można usunąć <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> atrybut z pola, a <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>następnie wywołać .

#### <a name="category"></a>Kategoria

CoreFx

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
