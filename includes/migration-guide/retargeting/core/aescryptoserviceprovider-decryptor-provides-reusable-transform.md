---
ms.openlocfilehash: 846a6bcd3c668e6ad505f745bcb830c3b9dce437
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859341"
---
### <a name="aescryptoserviceprovider-decryptor-provides-a-reusable-transform"></a>Odszyfrowujący AesCryptoServiceProvider zapewnia przekształcenie wielokrotnego użytku

|   |   |
|---|---|
|Szczegóły|Począwszy od aplikacji przeznaczonych dla platformy .NET Framework 4.6.2, <xref:System.Security.Cryptography.AesCryptoServiceProvider> odszyfrowujący umożliwia przekształcanie wielokrotnego użytku. Po wywołaniu <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=name>, przekształcenia są ponownie inicjowane i mogą być ponownie używane. W przypadku aplikacji przeznaczonych dla wcześniejszych wersji programu .NET Framework próba ponownego użycia odszyfrowujący, wywołując <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=name> po wywołaniu <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=name> zgłasza <xref:System.Security.Cryptography.CryptographicException> lub uszkodzone dane.|
|Sugestia|Wpływ tej zmiany należy minimalny, ponieważ jest to oczekiwane zachowanie. Aplikacje, które są zależne od poprzedniego zachowania można zrezygnować z jej korzystania z niego, dodając następujące ustawienie konfiguracji, aby <code>&lt;runtime&gt;</code> sekcję pliku konfiguracji aplikacji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Ponadto aplikacje odwoływać się do poprzedniej wersji programu .NET Framework, które są uruchomione w wersji programu .NET Framework, począwszy od .NET Framework 4.6.2 zgodzić się na go, dodając następujące ustawienie konfiguracji, aby <code>&lt;runtime&gt;</code> sekcji plik konfiguracji aplikacji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Scope|Mały|
|Wersja|4.6.2|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor?displayProperty=nameWithType></li></ul>|

