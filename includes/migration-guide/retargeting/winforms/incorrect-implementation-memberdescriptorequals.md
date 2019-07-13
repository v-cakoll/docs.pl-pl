---
ms.openlocfilehash: 2413e1997b6e729b9d5889677e25254aaa24afea
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859363"
---
### <a name="incorrect-implementation-of-memberdescriptorequals"></a>Nieprawidłowa implementacja MemberDescriptor.Equals

|   |   |
|---|---|
|Szczegóły|Oryginalnej implementacji <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> metoda porównanie dwóch właściwości inny ciąg z obiektów, którą jest porównywany: Nazwa kategorii i ciąg opisu. Poprawka jest porównanie <xref:System.ComponentModel.MemberDescriptor.Category> pierwszego obiektu do <xref:System.ComponentModel.MemberDescriptor.Category> drugi z nich oraz <xref:System.ComponentModel.MemberDescriptor.Description> pierwszego do <xref:System.ComponentModel.MemberDescriptor.Description> drugiego.|
|Sugestia|Jeśli aplikacja jest zależna od <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> czasami zwracanie <code>false</code> po deskryptory są równoważne i są przeznaczone dla platformy .NET Framework 4.6.2 lub nowszy, masz kilka opcji:<ol><li>Wprowadzasz zmiany kodu, aby porównać <xref:System.ComponentModel.MemberDescriptor.Category> i <xref:System.ComponentModel.MemberDescriptor.Description> pól ręcznie oprócz wywoływania <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> metody.</li><li>Zrezygnować z tej zmiany, dodając następującą wartość do pliku app.config:</li></ol><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Jeśli aplikacja jest przeznaczony dla platformy .NET Framework 4.6.1 lub starszy i działa w środowisku .NET Framework 4.6.2 lub nowszy i chcesz, aby ta zmiana włączone, można ustawić przełącznik zgodności <code>false</code> , dodając następującą wartość do pliku app.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Scope|Krawędź|
|Wersja|4.6.2|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.ComponentModel.MemberDescriptor.Equals(System.Object)?displayProperty=nameWithType></li></ul>|

