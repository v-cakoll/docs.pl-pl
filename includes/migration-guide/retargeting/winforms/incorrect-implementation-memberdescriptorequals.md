---
ms.openlocfilehash: 01c0689bbfb102f8f4d9455f9d258e8ea5515d9e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859363"
---
### <a name="incorrect-implementation-of-memberdescriptorequals"></a>Niepoprawna implementacja deskryptora.Równy

|   |   |
|---|---|
|Szczegóły|Oryginalna implementacja <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> metody porównuje dwie różne właściwości ciągu z porównywanych obiektów: nazwę kategorii i ciąg opisu. <xref:System.ComponentModel.MemberDescriptor.Category> Poprawka jest porównanie pierwszego obiektu do <xref:System.ComponentModel.MemberDescriptor.Category> drugiego, a <xref:System.ComponentModel.MemberDescriptor.Description> pierwszy <xref:System.ComponentModel.MemberDescriptor.Description> do drugiego.|
|Sugestia|Jeśli aplikacja zależy <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> od <code>false</code> czasami zwracane, gdy deskryptory są równoważne i są przeznaczone dla .NET Framework 4.6.2 lub nowsze, masz kilka opcji:<ol><li>Wprowadzać zmiany kodu, aby porównać <xref:System.ComponentModel.MemberDescriptor.Category> i <xref:System.ComponentModel.MemberDescriptor.Description> <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> pola ręcznie oprócz wywoływania metody.</li><li>Zrezygnuj z tej zmiany, dodając następującą wartość do pliku app.config:</li></ol><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Jeśli aplikacja jest przeznaczona dla platformy .NET Framework 4.6.1 lub wcześniejszej i jest uruchomiona w programie .NET Framework 4.6.2 lub nowszym i ma być włączona ta zmiana, można ustawić przełącznik <code>false</code> zgodności, dodając następującą wartość do pliku app.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Brzeg|
|Wersja|4.6.2|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.ComponentModel.MemberDescriptor.Equals(System.Object)?displayProperty=nameWithType></li></ul>|
