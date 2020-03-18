---
ms.openlocfilehash: d48ced9d0201a33f9149aba155ddd3d8bc04c93f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74643957"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a>SerializableAttribute usunięte z niektórych typów formularzy systemu Windows

Został <xref:System.SerializableAttribute> usunięty z niektórych klas formularzy systemu Windows, które nie mają znanych scenariuszy serializacji binarnej.

#### <a name="change-description"></a>Zmień opis

Następujące typy są ozdobione <xref:System.SerializableAttribute> w .NET Framework, ale atrybut został usunięty w .NET Core:

- `System.InvariantComparer`
- <xref:System.ComponentModel.Design.ExceptionCollection?displayProperty=nameWithType>
- <xref:System.ComponentModel.Design.Serialization.CodeDomSerializerException?displayProperty=nameWithType>
- `System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService.CodeDomSerializationStore`
- <xref:System.Drawing.Design.ToolboxItem?displayProperty=nameWithType>
- `System.Resources.ResXNullRef`
- `System.Resources.ResXDataNode`
- `System.Resources.ResXFileRef`
- <xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>
- `System.Windows.Forms.NativeMethods.MSOCRINFOSTRUCT`
- `System.Windows.Forms.NativeMethods.MSG`

Historycznie ten mechanizm serializacji miał poważne problemy z konserwacją i bezpieczeństwem. Utrzymywanie `SerializableAttribute` na typy oznacza, że te typy muszą być testowane pod kątem zmian serializacji wersji do wersji i potencjalnie framework-to-framework zmiany serializacji. To sprawia, że trudniej rozwijać te typy i może być kosztowne w utrzymaniu. Te typy nie mają znanych scenariuszy serializacji binarnych, co minimalizuje wpływ usuwania atrybutu.

Aby uzyskać więcej informacji, zobacz [Serializacja binarna](~/docs/standard/serialization/binary-serialization.md).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0 Podgląd 9

#### <a name="recommended-action"></a>Zalecana akcja

Zaktualizuj dowolny kod, który może zależeć od tych typów są oznaczone jako serializacji.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- Brak

<!--

### Affected APIs

- Not detectable via API analysis

-->
