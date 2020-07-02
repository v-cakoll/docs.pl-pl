---
ms.openlocfilehash: 36a9db601f7637185bf48dfcbe2233b4489fcdcf
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614658"
---
### <a name="aescryptoserviceprovider-decryptor-provides-a-reusable-transform"></a>Deszyfrowanie AesCryptoServiceProvider zapewnia przekształcenie wielokrotnego użytku

#### <a name="details"></a>Szczegóły

Począwszy od aplikacji, które są przeznaczone dla .NET Framework 4.6.2, <xref:System.Security.Cryptography.AesCryptoServiceProvider> deszyfrowanie zapewnia przekształcenie wielokrotnego użytku. Po wywołaniu <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> , transformacja zostanie zainicjowana i może być ponownie użyta. W przypadku aplikacji, które są przeznaczone dla wcześniejszych wersji .NET Framework, próba ponownego użycia deszyfrującego przez wywołanie metody wyrzucania <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=fullName> <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> <xref:System.Security.Cryptography.CryptographicException> lub powoduje uszkodzenie danych.

#### <a name="suggestion"></a>Sugestia

Wpływ tej zmiany powinien być minimalny, ponieważ jest to oczekiwane zachowanie. Aplikacje, które są zależne od poprzedniego zachowania, mogą zrezygnować z korzystania z niego, dodając następujące ustawienia konfiguracji do `<runtime>` sekcji pliku konfiguracyjnego aplikacji:

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true"/>
</runtime>
```

Ponadto aplikacje przeznaczone dla wcześniejszej wersji .NET Framework ale działają w ramach wersji .NET Framework, zaczynając od .NET Framework 4.6.2, dodając następujące ustawienia konfiguracji do `<runtime>` sekcji pliku konfiguracyjnego aplikacji:

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false"/>
</runtime>
```

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.6.2       |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor?displayProperty=nameWithType>
