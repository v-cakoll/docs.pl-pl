---
ms.openlocfilehash: c008809606372c84b05a2facd1cac1293382aed4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640137"
---
### <a name="aescryptoserviceprovider-decryptor-provides-a-reusable-transform"></a>Odszyfrowujący AesCryptoServiceProvider zapewnia przekształcenie wielokrotnego użytku

|   |   |
|---|---|
|Szczegóły|Począwszy od aplikacji przeznaczonych dla platformy .NET Framework 4.6.2, <xref:System.Security.Cryptography.AesCryptoServiceProvider> odszyfrowujący umożliwia przekształcanie wielokrotnego użytku. Po wywołaniu <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=name>, przekształcenia są ponownie inicjowane i mogą być ponownie używane. W przypadku aplikacji przeznaczonych dla wcześniejszych wersji programu .NET Framework próba ponownego użycia odszyfrowujący, wywołując <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=name> po wywołaniu <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=name> zgłasza <xref:System.Security.Cryptography.CryptographicException> lub uszkodzone dane.|
|Sugestia|Wpływ tej zmiany należy minimalny, ponieważ jest to oczekiwane zachowanie. Aplikacje, które są zależne od poprzedniego zachowania można zrezygnować z jej korzystania z niego, dodając następujące ustawienie konfiguracji, aby <code>&lt;runtime&gt;</code> sekcję pliku konfiguracji aplikacji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Ponadto aplikacje odwoływać się do poprzedniej wersji programu .NET Framework, które są uruchomione w wersji programu .NET Framework, począwszy od .NET Framework 4.6.2 zgodzić się na go, dodając następujące ustawienie konfiguracji, aby <code>&lt;runtime&gt;</code> sekcji plik konfiguracji aplikacji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.6.2|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor?displayProperty=nameWithType></li></ul>|
