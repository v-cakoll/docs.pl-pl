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
ms.openlocfilehash: 2db6d4229ac777801aff792c86fe0e5e9a1b4994
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2018
ms.locfileid: "45653294"
---
# <a name="creating-a-cryptographic-scheme"></a>Tworzenie schematu kryptograficznego
Można łączyć kryptograficznych składników .NET Framework do tworzenia różnych systemów do szyfrowania i odszyfrowywania danych.  
  
 Prosty schemat szyfrowania szyfrowanie i odszyfrowywanie danych może określić następujące czynności:  
  
1.  Każda ze stron generowana jest para kluczy publiczny/prywatny.  
  
2.  Strony wymiany kluczy publicznych.  
  
3.  Każda ze stron generuje klucz tajny dla celów szyfrowania TripleDES, na przykład i szyfruje nowo utworzony klucz przy użyciu klucza publicznego drugiej strony.  
  
4.  Każda strona wysyła dane do drugiego i łączy klucz tajny drugiej strony z własną, w szczególności kolejności, aby utworzyć nowy klucz tajny.  
  
5.  Strony następnie zainicjuj konwersacji za pomocą szyfrowania symetrycznego.  
  
 Tworzenie schematu kryptograficznego nie jest prostym zadaniem. Aby uzyskać więcej informacji na temat korzystania z szyfrowania, zobacz temat kryptografii w dokumentacji platformy SDK pod adresem http://msdn.microsoft.com/library.  
  
## <a name="see-also"></a>Zobacz także

- [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)
