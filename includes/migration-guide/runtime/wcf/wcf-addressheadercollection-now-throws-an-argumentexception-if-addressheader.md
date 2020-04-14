---
ms.openlocfilehash: fa2a856911c7dcf81a39b7682a62a86c35328037
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275378"
---
### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a>WCF AddressHeaderCollection teraz zgłasza ArgumentException, jeśli addressHeader element jest null

|   |   |
|---|---|
|Szczegóły|Począwszy od .NET Framework 4.7.1, <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> konstruktor <xref:System.ArgumentException> zgłasza, <code>null</code>jeśli jeden z elementów jest . W .NET Framework 4.7 i wcześniejszych wersjach nie jest zgłaszany żaden wyjątek.|
|Sugestia|Jeśli wystąpią problemy ze zgodnością z tą zmianą w programie .NET Framework 4.7.1 lub nowszej <code>&lt;runtime&gt;</code> wersji, możesz zrezygnować z niej, dodając następujący wiersz do sekcji pliku app.config::<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.7.1|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})></li></ul>|
