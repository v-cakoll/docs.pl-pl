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
ms.openlocfilehash: b1635276465dd58028c8a5e4b7e69a307664a4c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580760"
---
# <a name="creating-a-cryptographic-scheme"></a>Tworzenie schematu kryptograficznego
Do tworzenia różnych programów do szyfrowania i odszyfrowywania danych można łączyć kryptograficznych składników platformy .NET.  
  
 Proste schematu kryptograficznego do szyfrowania i odszyfrowywania danych może określać następujące czynności:  
  
1.  Każda strona generuje pary kluczy publiczny/prywatny.  
  
2.  Strony wymiany kluczy publicznych.  
  
3.  Każda strona generuje klucz tajny dla celów szyfrowania TripleDES, na przykład i szyfruje klucz nowo utworzony przy użyciu klucza publicznego drugiego.  
  
4.  Strony wysyła dane do innych i łączy klucz tajny drugiego z własnej, w szczególności kolejność, aby utworzyć nowy klucz tajny.  
  
5.  Strony inicjuje konwersację za pomocą szyfrowania symetrycznego.  
  
 Tworzenie schematu kryptograficznego manipulacji nie jest prosta. Aby uzyskać więcej informacji na temat używania kryptografii, zobacz temat kryptografii w dokumentacji zestawu SDK platformy w http://msdn.microsoft.com/library.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)
