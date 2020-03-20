---
ms.openlocfilehash: c008809606372c84b05a2facd1cac1293382aed4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859341"
---
### <a name="aescryptoserviceprovider-decryptor-provides-a-reusable-transform"></a>Deszyfrator AesCryptoServiceProvider zapewnia transformację wielokrotnego

|   |   |
|---|---|
|Szczegóły|Począwszy od aplikacji, które są przeznaczone dla programu .NET Framework 4.6.2, <xref:System.Security.Cryptography.AesCryptoServiceProvider> deszyfrator zapewnia transformację wielokrotnego pożytu. Po wywołaniu <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=name>, transformacja jest ponownie initialized i może być ponownie. W przypadku aplikacji przeznaczonych dla wcześniejszych wersji programu .NET Framework próba <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=name> ponownego użycia <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=name> deszyfratora przez wywołanie po wywołaniu, aby zgłosić <xref:System.Security.Cryptography.CryptographicException> lub produkuje uszkodzone dane.|
|Sugestia|Wpływ tej zmiany powinien być minimalny, ponieważ jest to oczekiwane zachowanie. Aplikacje, które zależą od poprzedniego zachowania, mogą zrezygnować z niego, używając go, dodając następujące ustawienie konfiguracji do <code>&lt;runtime&gt;</code> sekcji pliku konfiguracyjnego aplikacji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Ponadto aplikacje przeznaczone dla poprzedniej wersji programu .NET Framework, ale działające w wersji programu .NET Framework, zaczynając od programu .NET Framework 4.6.2, mogą wyrazić zgodę, dodając następujące ustawienie konfiguracji do <code>&lt;runtime&gt;</code> sekcji pliku konfiguracyjnego aplikacji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.6.2|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor?displayProperty=nameWithType></li></ul>|
