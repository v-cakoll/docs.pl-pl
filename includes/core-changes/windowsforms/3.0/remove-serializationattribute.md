---
ms.openlocfilehash: d48ced9d0201a33f9149aba155ddd3d8bc04c93f
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643957"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a>SerializableAttribute usunięte z niektórych typów Windows Forms

<xref:System.SerializableAttribute> został usunięty z niektórych klas Windows Forms, które nie mają znanych scenariuszy serializacji binarnej.

#### <a name="change-description"></a>Zmień opis

Następujące typy są dekoracyjne <xref:System.SerializableAttribute> w .NET Framework, ale atrybut został usunięty z platformy .NET Core:

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

W przeszłości ten mechanizm serializacji miał poważne problemy związane z konserwacją i bezpieczeństwem. Obsługa `SerializableAttribute` w typach oznacza, że te typy muszą być testowane pod kątem zmian serializacji z wersji do wersji oraz ewentualnych zmian serializacji między platformami. Dzięki temu trudniej jest rozwijać te typy i mogą być kosztowne do utrzymania. Te typy nie mają znanych scenariuszy serializacji binarnej, co minimalizuje wpływ usuwania atrybutu.

Aby uzyskać więcej informacji, zobacz [Serializacja binarna](~/docs/standard/serialization/binary-serialization.md).

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 9

#### <a name="recommended-action"></a>Zalecane działanie

Zaktualizuj każdy kod, który może zależeć od tych typów jako możliwy do serializacji.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- Brak

<!--

### Affected APIs

- Not detectable via API analysis

-->
