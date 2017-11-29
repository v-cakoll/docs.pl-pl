---
title: Tworzenie schematu kryptograficznego
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3e3c4a832f70fae7808bf71016cb9f6648332f01
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="creating-a-cryptographic-scheme"></a>Tworzenie schematu kryptograficznego
Do tworzenia różnych programów do szyfrowania i odszyfrowywania danych można łączyć kryptograficznych składników platformy .NET.  
  
 Proste schematu kryptograficznego do szyfrowania i odszyfrowywania danych może określać następujące czynności:  
  
1.  Każda strona generuje pary kluczy publiczny/prywatny.  
  
2.  Strony wymiany kluczy publicznych.  
  
3.  Każda strona generuje klucz tajny dla celów szyfrowania TripleDES, na przykład i szyfruje klucz nowo utworzony przy użyciu klucza publicznego drugiego.  
  
4.  Strony wysyła dane do innych i łączy klucz tajny drugiego z własnej, w szczególności kolejność, aby utworzyć nowy klucz tajny.  
  
5.  Strony inicjuje konwersację za pomocą szyfrowania symetrycznego.  
  
 Tworzenie schematu kryptograficznego manipulacji nie jest prosta. Aby uzyskać więcej informacji na temat używania kryptografii zobacz temat kryptografii w dokumentacji zestawu SDK platformy w http://msdn.microsoft.com/library/.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)
