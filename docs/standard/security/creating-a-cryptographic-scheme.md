---
title: Tworzenie schematu kryptograficznego
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ef3741ef5cec720c2fb285c9aa60d610acc0be9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59321656"
---
# <a name="creating-a-cryptographic-scheme"></a>Tworzenie schematu kryptograficznego
Można łączyć kryptograficznych składników .NET Framework do tworzenia różnych systemów do szyfrowania i odszyfrowywania danych.  
  
 Prosty schemat szyfrowania szyfrowanie i odszyfrowywanie danych może określić następujące czynności:  
  
1. Każda ze stron generowana jest para kluczy publiczny/prywatny.  
  
2. Strony wymiany kluczy publicznych.  
  
3. Każda ze stron generuje klucz tajny dla celów szyfrowania TripleDES, na przykład i szyfruje nowo utworzony klucz przy użyciu klucza publicznego drugiej strony.  
  
4. Każda strona wysyła dane do drugiego i łączy klucz tajny drugiej strony z własną, w szczególności kolejności, aby utworzyć nowy klucz tajny.  
  
5. Strony następnie zainicjuj konwersacji za pomocą szyfrowania symetrycznego.  
  
 Tworzenie schematu kryptograficznego nie jest prostym zadaniem.
  
## <a name="see-also"></a>Zobacz także

- [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)
