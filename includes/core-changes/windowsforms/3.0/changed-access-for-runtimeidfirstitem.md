---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74644048"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a>Zmiana dostępu dla accessibleObject.RuntimeIDFirstItem

Począwszy od .NET Core 3.0 `AccessibleObject.RuntimeIDFirstItem` RC1, `protected` `internal`dostępność została zmieniona z .

#### <a name="change-description"></a>Zmień opis

Począwszy od .NET Core 3.0 Preview 4, `AccessibleObject.RuntimeIDFirstItem` pole było `protected`. Począwszy od .NET Core 3.0 RC1, został zmieniony z `protected` na wyrównanie `internal` z dostępnością pola w .NET Framework.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0 Rc1

#### <a name="recommended-action"></a>Zalecana akcja

Zmiana może mieć wpływ, jeśli opracowano aplikację .NET Core z <xref:System.Windows.Forms.AccessibleObject> typem, `RuntimeIDFirstItem` który pochodzi od pola i uzyskuje dostęp do niego. W takim przypadku można zdefiniować stałą lokalną w następujący sposób:

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- Nie wykrywalne za pomocą analizy Interfejsu API.

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
