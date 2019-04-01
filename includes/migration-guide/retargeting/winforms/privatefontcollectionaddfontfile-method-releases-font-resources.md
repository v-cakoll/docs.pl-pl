---
ms.openlocfilehash: c923d9b341bbf0a21d73ac75cc6cb1a037f37826
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760861"
---
### <a name="privatefontcollectionaddfontfile-method-releases-font-resources"></a>Metoda PrivateFontCollection.AddFontFile zwalnia zasoby czcionki

|   |   |
|---|---|
|Szczegóły|.NET Framework 4.7.1 i poprzednich wersjach <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> klasy nie spowoduje zwolnienia zasobów czcionki GDI + po <xref:System.Drawing.Text.PrivateFontCollection> zostanie usunięty, aby uzyskać <xref:System.Drawing.Font> obiekty, które są dodawane do tej kolekcji przy użyciu <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)> metody. W programie .NET Framework 4.7.2 i nowszych <xref:System.Drawing.Text.FontCollection.Dispose%2A> zwalnia czcionki GDI +, które zostały dodane do kolekcji jako plików.|
|Sugestia|<strong>Sposób korzystania z opcji na lub poza te zmiany</strong>w kolejności dla aplikacji, aby korzystać z tych zmian, należy uruchomić w środowisku .NET Framework 4.7.2 lub nowszej. Aplikacji mogą korzystać z tych zmian w jednej z następujących sposobów:<ul><li>Jest ponownie kompilowana pod kątem programu .NET Framework 4.7.2. Ta zmiana jest włączona domyślnie w aplikacji Windows Forms, przeznaczonych dla środowiska .NET Framework 4.7.2 lub nowszej.</li><li>Jest przeznaczony dla platformy .NET Framework 4.7.1 lub starszej wersji, a zdecyduje poza zachowania starszych ułatwień dostępu przez dodanie poniższego [przełącznika AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do <code>&lt;runtime&gt;</code> sekcji w pliku app.config i ustawieniem dla niego <code>false</code>, jak pokazano w poniższym przykładzie.</li></ul><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Drawing.Text.DoNotRemoveGdiFontsResourcesFromFontCollection=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Aplikacji przeznaczonych dla środowiska .NET Framework 4.7.2 lub nowszy i chcesz zachować starsze zachowanie zgodzić się na nie zwolnienia zasobów czcionki przez jawne ustawienie tego parametru AppContext <code>true</code>.|
|Zakres|Krawędź|
|Wersja|4.7.2|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType></li><li><xref:System.Drawing.Text.FontCollection.Dispose?displayProperty=nameWithType></li></ul>|

