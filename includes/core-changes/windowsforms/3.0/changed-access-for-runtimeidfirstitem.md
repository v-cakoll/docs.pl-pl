---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644048"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a>Zmiana dostępu do elementu AccessibleObject. RuntimeIDFirstItem

Począwszy od platformy .NET Core 3,0 RC1, dostępność `AccessibleObject.RuntimeIDFirstItem` została zmieniona z `protected` na `internal`.

#### <a name="change-description"></a>Zmień opis

Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 4, pole `AccessibleObject.RuntimeIDFirstItem` zostało `protected`. Począwszy od programu .NET Core 3,0 RC1, zmienił się z `protected` na `internal`, aby wyrównać dostępność pola w .NET Framework.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 RC1

#### <a name="recommended-action"></a>Zalecane działanie

Ta zmiana może mieć wpływ na użytkownika, jeśli opracowano aplikację .NET Core z typem pochodzącym z <xref:System.Windows.Forms.AccessibleObject> i uzyskuje dostęp do pola `RuntimeIDFirstItem`. W takim przypadku można zdefiniować stałą lokalną w następujący sposób:

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- Nie wykrywalne za pośrednictwem analizy interfejsu API.

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
