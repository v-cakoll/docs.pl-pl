---
title: Tworzenie schematu kryptograficznego
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
ms.openlocfilehash: 1478873c1c2dc73ca31c9078e39a3902966bf674
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288423"
---
# <a name="creating-a-cryptographic-scheme"></a>Tworzenie schematu kryptograficznego
Składniki kryptograficzne .NET Framework można łączyć w celu tworzenia różnych schematów do szyfrowania i odszyfrowywania danych.  
  
 Prosty schemat kryptograficzny służący do szyfrowania i odszyfrowywania danych może zawierać następujące czynności:  
  
1. Każda ze stron generuje parę kluczy publiczny/prywatny.  
  
2. Strony wymieniają swoje klucze publiczne.  
  
3. Każda ze stron generuje klucz tajny na potrzeby szyfrowania TripleDES, na przykład i szyfruje nowo utworzony klucz przy użyciu klucza publicznego drugiego.  
  
4. Każda ze stron wysyła dane do drugiej i łączy klucz tajny z własnym, w określonej kolejności, w celu utworzenia nowego klucza tajnego.  
  
5. Następnie strony inicjują konwersację przy użyciu szyfrowania symetrycznego.  
  
 Tworzenie schematu kryptograficznego nie jest zadaniem prostym.
  
## <a name="see-also"></a>Zobacz także

- [Usługi kryptograficzne](cryptographic-services.md)
