---
title: Szyfrowanie i odszyfrowywanie ciągów w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: 96e56ab315a739fef9d5499b076a077f5294f39e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a>Wskazówki: szyfrowanie i odszyfrowywanie ciągów w Visual Basic
Ten przewodnik przedstawia sposób użycia <xref:System.Security.Cryptography.DESCryptoServiceProvider> klasy do szyfrowania i odszyfrowywania ciągów za pomocą wersji dostawcy usług kryptograficznych Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algorytmu. Pierwszym krokiem jest można utworzyć klasy otoki proste, który hermetyzuje algorytmu 3DES i przechowuje zaszyfrowane dane jako ciąg zakodowany base-64. Następnie tej otoki służy bezpiecznie przechowywać prywatnych danych użytkowników w pliku tekstowym publicznie.  
  
 Należy używać szyfrowania, aby chronić hasła użytkownika (na przykład hasła) i wprowadzić poświadczenia niemożliwe do odczytania przez nieautoryzowanych użytkowników. To może chronić tożsamość autoryzowanym użytkownikiem z skradzione, która chroni zasoby użytkownika oraz udostępnia wyłączność podpisu. Szyfrowanie można również ochronę danych użytkownika z uzyskiwany przez nieautoryzowanych użytkowników.  
  
 Aby uzyskać więcej informacji, zobacz [usługi kryptograficzne](../../../../standard/security/cryptographic-services.md).  
  
> [!IMPORTANT]
>  Algorytmy Triple Data Encryption Standard (3DES) i Rijndael (teraz nazywane Advanced Encryption Standard [AES]) zawiera większe bezpieczeństwo niż metoda DES, ponieważ są one więcej znacznym w praktyce. Aby uzyskać więcej informacji, zobacz <xref:System.Security.Cryptography.DES> i <xref:System.Security.Cryptography.Rijndael>.  
  
### <a name="to-create-the-encryption-wrapper"></a>Aby utworzyć otoki szyfrowania  
  
1.  Utwórz `Simple3Des` klasy w celu hermetyzacji metody szyfrowania i odszyfrowywania.  
  
     [!code-vb[VbVbalrStrings#38](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]  
  
2.  Dodaj importu kryptografii przestrzeni nazw na początku pliku, który zawiera `Simple3Des` klasy.  
  
     [!code-vb[VbVbalrStrings#77](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]  
  
3.  W `Simple3Des` klasy, Dodaj pole prywatne do przechowywania 3DES dostawcy usług kryptograficznych.  
  
     [!code-vb[VbVbalrStrings#39](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]  
  
4.  Dodaj metody prywatnej, która tworzy tablicę bajtów o określonej długości ze skrótu określonego klucza.  
  
     [!code-vb[VbVbalrStrings#41](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]  
  
5.  Dodaj Konstruktor do zainicjowania dostawcy usług kryptograficznych 3DES.  
  
     `key` Sterowania parametrami `EncryptData` i `DecryptData` metody.  
  
     [!code-vb[VbVbalrStrings#40](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]  
  
6.  Dodaj publiczną metodę, który szyfruje ciąg.  
  
     [!code-vb[VbVbalrStrings#42](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]  
  
7.  Dodaj publiczną metodę odszyfrowujący ciąg.  
  
     [!code-vb[VbVbalrStrings#43](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]  
  
     Klasa otoki można teraz używać do ochrony zasobów użytkownika. W tym przykładzie jest używany bezpiecznie przechowywać prywatnych danych użytkowników w pliku tekstowym publicznie.  
  
### <a name="to-test-the-encryption-wrapper"></a>Aby przetestować otoki szyfrowania  
  
1.  W osobnej klasy, Dodaj metody, która używa otoki `EncryptData` metodę szyfrowania ciągu i zapisać go do użytkownika do folderu Moje dokumenty.  
  
     [!code-vb[VbVbalrStrings#78](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]  
  
2.  Dodaj metodę, która odczytuje zaszyfrowanego ciągu użytkownika do folderu Moje dokumenty i odszyfrowuje ciągu z otoką `DecryptData` metody.  
  
     [!code-vb[VbVbalrStrings#79](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]  
  
3.  Dodaj kod interfejsu użytkownika do wywołania `TestEncoding` i `TestDecoding` metody.  
  
4.  Uruchom aplikację.  
  
     Podczas testowania aplikacji, zwróć uwagę, że jej nie powoduje odszyfrowania danych Jeśli podasz nieprawidłowe hasło.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.Cryptography>  
 <xref:System.Security.Cryptography.DESCryptoServiceProvider>  
 <xref:System.Security.Cryptography.DES>  
 <xref:System.Security.Cryptography.TripleDES>  
 <xref:System.Security.Cryptography.Rijndael>  
 [Usługi kryptograficzne](../../../../standard/security/cryptographic-services.md)
