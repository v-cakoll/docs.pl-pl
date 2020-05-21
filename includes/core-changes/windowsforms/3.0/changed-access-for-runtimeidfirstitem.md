---
ms.openlocfilehash: 1ea2d70a7cfe04cc4c4b9b58ea6bb6fa0226b245
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721630"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a>Zmiana dostępu do elementu AccessibleObject. RuntimeIDFirstItem

Począwszy od platformy .NET Core 3,0 RC1, dostępność programu `AccessibleObject.RuntimeIDFirstItem` została zmieniona z `protected` na `internal` .

#### <a name="change-description"></a>Zmień opis

Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 4, `AccessibleObject.RuntimeIDFirstItem` pole było `protected` . Począwszy od platformy .NET Core 3,0 RC1, zmienił się z `protected` na, `internal` Aby wyrównać dostępność pola w .NET Framework.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 RC1

#### <a name="recommended-action"></a>Zalecana akcja

Ta zmiana może mieć wpływ na użytkownika, jeśli opracowano aplikację .NET Core z typem pochodzącym z <xref:System.Windows.Forms.AccessibleObject> i uzyskuje dostęp do `RuntimeIDFirstItem` pola. W takim przypadku można zdefiniować stałą lokalną w następujący sposób:

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- Nie wykrywalne za pośrednictwem analizy interfejsu API.

<!-- 

#### Affected APIs

- Not detectable via API analysis.

-->
