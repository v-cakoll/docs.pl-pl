---
title: 'Instrukcje: Dostęp do sprzętowych urządzeń szyfrujących'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encryption
- key card
- cryptography
- hardware encryption
- CspParameters
ms.assetid: b0e734df-6eb4-4b16-b48c-6f0fe82d5f17
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9c16c994e3976fb3ee569799461db1d1789a6186
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64654383"
---
# <a name="how-to-access-hardware-encryption-devices"></a>Instrukcje: Dostęp do sprzętowych urządzeń szyfrujących
Możesz użyć <xref:System.Security.Cryptography.CspParameters> klasy, aby dostęp do sprzętowych urządzeń szyfrujących. Na przykład można użyć tej klasy można zintegrować aplikację z karty inteligentnej, sprzęt generator liczb losowych lub z implementacją sprzętu określonego algorytmu kryptograficznego.  
  
 <xref:System.Security.Cryptography.CspParameters> Klasy tworzy dostawcy usług kryptograficznych (CSP), który uzyskuje dostęp do urządzenia szyfrowania sprzętowego poprawnie zainstalowane.  Możesz sprawdzić dostępność dostawcy usług Kryptograficznych, sprawdzając następujący klucz rejestru za pomocą Edytora rejestru (Regedit.exe):  HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.  
  
### <a name="to-sign-data-using-a-key-card"></a>Aby zarejestrować dane przy użyciu karta klucza  
  
1. Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.CspParameters> klasy, przekazując całkowitą typ dostawcy i nazwy dostawcy do konstruktora.  
  
2. Przekaż odpowiednie flagi, aby <xref:System.Security.Cryptography.CspParameters.Flags%2A> właściwości nowo utworzonej <xref:System.Security.Cryptography.CspParameters> obiektu.  Na przykład przekazać <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> flagi.  
  
3. Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.AsymmetricAlgorithm> klasy (na przykład <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasy), przekazując <xref:System.Security.Cryptography.CspParameters> obiekt do konstruktora.  
  
4. Zaloguj się do danych przy użyciu jednej z `Sign` metod i sprawdź swoje dane przy użyciu jednej z `Verify` metody.  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a>Aby wygenerować losową liczbę za pomocą sprzętu generator liczb losowych  
  
1. Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.CspParameters> klasy, przekazując całkowitą typ dostawcy i nazwy dostawcy do konstruktora.  
  
2. Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, przekazując <xref:System.Security.Cryptography.CspParameters> obiekt do konstruktora.  
  
3. Tworzenie przy użyciu wartości losowej <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> lub <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób rejestrowania danych przy użyciu karty inteligentnej.  Przykład kodu tworzy <xref:System.Security.Cryptography.CspParameters> obiekt, który udostępnia kart inteligentnych, a następnie inicjuje <xref:System.Security.Cryptography.RSACryptoServiceProvider> przy użyciu dostawcy usług Kryptograficznych.  W przykładzie kodu, a następnie podpisuje i weryfikuje niektórych danych.  
  
 [!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
 [!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
 [!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Obejmują <xref:System> i <xref:System.Security.Cryptography> przestrzeni nazw.  
  
- Konieczne jest posiadanie czytnik kart inteligentnych i sterowniki zainstalowane na tym komputerze.  
  
- Należy zainicjować <xref:System.Security.Cryptography.CspParameters> przy użyciu informacji specyficznych dla czytnika kart.  Więcej informacji na ten temat można znaleźć w dokumentacji czytnika kart.
