---
title: 'Porady: dostęp do sprzętowych urządzeń szyfrujących'
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
ms.openlocfilehash: d6ee22fd9fb0c11e22ac01ff83b3269e37e37763
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706178"
---
# <a name="how-to-access-hardware-encryption-devices"></a>Porady: dostęp do sprzętowych urządzeń szyfrujących
Aby uzyskać dostęp do urządzeń do szyfrowania sprzętu, można użyć klasy <xref:System.Security.Cryptography.CspParameters>. Na przykład można użyć tej klasy do zintegrowania aplikacji z kartą inteligentną, generatorem losowych liczb sprzętowych lub sprzętową implementacją określonego algorytmu kryptograficznego.  
  
 Klasa <xref:System.Security.Cryptography.CspParameters> tworzy dostawcę usług kryptograficznych (CSP), który uzyskuje dostęp do prawidłowo zainstalowanego urządzenia szyfrującego sprzętowego.  Dostępność dostawcy CSP można sprawdzić, sprawdzając następujący klucz rejestru przy użyciu Edytora rejestru (regedit. exe): HKEY_LOCAL_MACHINE \Software\Microsoft\Cryptography\Defaults\Provider.  
  
### <a name="to-sign-data-using-a-key-card"></a>Aby podpisać dane przy użyciu karty klucza  
  
1. Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.CspParameters>, przekazując typ dostawcy integer i nazwę dostawcy do konstruktora.  
  
2. Przekaż odpowiednie flagi do właściwości <xref:System.Security.Cryptography.CspParameters.Flags%2A> nowo utworzonego obiektu <xref:System.Security.Cryptography.CspParameters>.  Na przykład Przekaż flagę <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer>.  
  
3. Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.AsymmetricAlgorithm> (na przykład klasy <xref:System.Security.Cryptography.RSACryptoServiceProvider>), przekazując obiekt <xref:System.Security.Cryptography.CspParameters> do konstruktora.  
  
4. Podpisz swoje dane przy użyciu jednej z `Sign` metod i sprawdź swoje dane przy użyciu jednej z metod `Verify`.  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a>Aby wygenerować liczbę losową przy użyciu generatora liczb losowych sprzętowych  
  
1. Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.CspParameters>, przekazując typ dostawcy integer i nazwę dostawcy do konstruktora.  
  
2. Utwórz nowe wystąpienie <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, przekazując obiekt <xref:System.Security.Cryptography.CspParameters> do konstruktora.  
  
3. Utwórz wartość losową przy użyciu metody <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> lub <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób podpisywania danych przy użyciu karty inteligentnej.  Przykładowy kod tworzy obiekt <xref:System.Security.Cryptography.CspParameters>, który uwidacznia kartę inteligentną, a następnie inicjuje obiekt <xref:System.Security.Cryptography.RSACryptoServiceProvider> przy użyciu dostawcy CSP.  Przykład kodu następnie podpisuje i weryfikuje niektóre dane.  
  
 [!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
 [!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
 [!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Uwzględnij <xref:System> i <xref:System.Security.Cryptography> przestrzenie nazw.  
  
- Na komputerze musi być zainstalowany czytnik kart inteligentnych i sterowniki.  
  
- Należy zainicjować obiekt <xref:System.Security.Cryptography.CspParameters> przy użyciu informacji specyficznych dla czytnika kart.  Aby uzyskać więcej informacji, zobacz dokumentację czytnika kart.
