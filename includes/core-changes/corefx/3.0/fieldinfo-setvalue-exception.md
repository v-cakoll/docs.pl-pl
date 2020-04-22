---
ms.openlocfilehash: 9f8a790718fbb9d685bb8959808338dc1766bf2c
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021658"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a>FieldInfo.SetValue zgłasza wyjątek dla pól statycznych, tylko init

Począwszy od .NET Core 3.0, wyjątek jest zgłaszany podczas <xref:System.Reflection.FieldAttributes.InitOnly> próby ustawiania wartości na statycznym polu przez wywołanie <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.

#### <a name="change-description"></a>Zmień opis

W programach .NET Framework i wersjach programu .NET Core przed wersją 3.0 można ustawić wartość pola statycznego, które <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>jest stałe po jego zainicjowaniu[(odczytanym tylko w języku C#),](~/docs/csharp/language-reference/keywords/readonly.md)wywołując program . Jednak ustawienie takiego pola w ten sposób spowodowało nieprzewidywalne zachowanie na podstawie struktury docelowej i ustawień optymalizacji.

W .NET Core 3.0 i nowszych wersjach, po wywołaniu <xref:System.Reflection.FieldInfo.SetValue%2A> na statyczne, <xref:System.Reflection.FieldAttributes.InitOnly> pole, <xref:System.FieldAccessException?displayProperty=nameWithType> wyjątek.

> [!TIP]
> Pole <xref:System.Reflection.FieldAttributes.InitOnly> jest takie, które można ustawić tylko w momencie jego deklarowania lub w konstruktorze dla klasy zawierającej. Innymi słowy, jest stała po zainicjowaniu.

#### <a name="version-introduced"></a>Wprowadzono wersję

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Inicjuj <xref:System.Reflection.FieldAttributes.InitOnly> statyczne pola w konstruktorze statycznym. Dotyczy to zarówno typów dynamicznych, jak i niedynamikowych.

Alternatywnie można usunąć <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> atrybut z pola, a <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>następnie wywołać .

#### <a name="category"></a>Kategoria

Podstawowe biblioteki .NET

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
