---
ms.openlocfilehash: 2cd107dc92fd0fae89717c38840ce7ea44f3ac9a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640116"
---
### <a name="wpf-changing-a-primary-key-when-displaying-ado-data-in-a-masterdetail-scenario"></a>WPF, zmiana klucza podstawowego, podczas wyświetlania danych ADO w scenariuszu wzorzec/szczegół

|   |   |
|---|---|
|Szczegóły|Załóżmy, że masz ADO zbiór elementów typu <code>Order</code>, przy użyciu relacji o nazwie &quot;OrderDetails&quot; dotyczą zbiór elementów typu <code>Detail</code> za pomocą klucza podstawowego &quot;OrderID&quot;. W aplikacji WPF można powiązać kontrolkę listy do szczegółów dla podanej kolejności:<pre><code class="lang-xml">&lt;ListBox ItemsSource=&quot;{Binding Path=OrderDetails}&quot; &gt;&#13;&#10;</code></pre>w przypadku kontekstu danych <code>Order</code>. WPF pobiera wartość <code>OrderDetails</code> właściwość — zbierania D wszystkich <code>Detail</code> elementów, których <code>OrderID</code> odpowiada <code>OrderID</code> elementu głównego. Zmiana zachowania pojawia się podczas zmiany klucza podstawowego <code>OrderID</code> elementu głównego. Automatycznie zmienia ADO <code>OrderID</code> każdego odpowiednie rekordy w kolekcji szczegółów (to znaczy te skopiowane do kolekcji D).  Ale co się dzieje z D?<ul><li>Stare zachowanie:   Kolekcja D jest wyczyszczone.   Element główny jest <em>nie</em> zgłosić powiadomienia o zmianach dotyczącego właściwości <code>OrderDetails</code>.  Pole listy w dalszym ciągu używać kolekcji D, który jest obecnie pusta.</li><li>Nowe zachowanie:  Kolekcja D jest bez zmian.   Każdy z jego elementów zgłasza powiadomienia o zmianach dotyczącego <code>OrderID</code> właściwości.  Pole listy będzie później nadal używać kolekcji D, a następnie wyświetla szczegółowe informacje przy użyciu nowego <code>OrderID</code>.</li></ul>WPF implementuje nowe zachowanie przez utworzenie kolekcji D w inny sposób: przez wywołanie metody ADO <xref:System.Data.DataRowView.CreateChildView(System.Data.DataRelation,System.Boolean)?displayProperty=nameWithType> z <code>followParent</code> argument wartość <code>true</code>.|
|Sugestia|Aplikacja pobiera nowe zachowanie przy użyciu następującego przełącznika AppContext.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.DoNotUseFollowParentWhenBindingToADODataRelation=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;&#13;&#10;</code></pre>Wartością domyślną jest przełącznik <code>true</code> (stare zachowanie) dla aplikacji przeznaczonych dla platformy .NET 4.7.1 lub w dół i <code>false</code> (nowe zachowanie) dla aplikacji przeznaczonych dla platformy .NET 4.7.2 lub nowszej.|
|Zakres|Mały|
|Wersja|4.7.2|
|Typ|Przekierowanie|
