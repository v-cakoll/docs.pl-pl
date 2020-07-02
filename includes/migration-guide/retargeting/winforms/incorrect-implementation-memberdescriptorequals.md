---
ms.openlocfilehash: 2d0798917b639bc90bf3f78f6fb9f19d0eaf2c71
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614819"
---
### <a name="incorrect-implementation-of-memberdescriptorequals"></a>Niepoprawna implementacja MemberDescriptor. Equals

#### <a name="details"></a>Szczegóły

Oryginalna implementacja <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> metody porównuje dwie różne właściwości ciągu z obiektów, które są porównywane: Nazwa kategorii i ciąg opisu. Poprawka polega na poprawieniu <xref:System.ComponentModel.MemberDescriptor.Category> pierwszego obiektu do <xref:System.ComponentModel.MemberDescriptor.Category> drugiego, a <xref:System.ComponentModel.MemberDescriptor.Description> pierwszy do <xref:System.ComponentModel.MemberDescriptor.Description> drugiego w drugim.

#### <a name="suggestion"></a>Sugestia

Jeśli aplikacja jest zależna od <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> czasem `false` , gdy deskryptory są równoważne, a użytkownik jest ukierunkowany na .NET Framework 4.6.2 lub nowszy, masz kilka opcji:

- Wprowadź zmiany w kodzie, aby <xref:System.ComponentModel.MemberDescriptor.Category> porównać <xref:System.ComponentModel.MemberDescriptor.Description> pola i ręcznie oprócz wywoływania <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> metody.
- Zrezygnuj z tej zmiany, dodając następującą wartość do pliku app.config:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true" />
</runtime>
```

Jeśli aplikacja jest przeznaczona .NET Framework 4.6.1 lub wcześniejsza i jest uruchomiona na .NET Framework 4.6.2 lub nowszej i chcesz, aby ta zmiana została włączona, można ustawić przełącznik zgodności, `false` dodając następującą wartość do pliku app.config:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=false" />
</runtime>
```

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4.6.2       |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.ComponentModel.MemberDescriptor.Equals(System.Object)?displayProperty=nameWithType>
