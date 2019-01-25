---
title: Szyfrowanie i odszyfrowywanie ciągów w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: ee3bcd1358536e6fd9bed5c4fec7845fdf441d86
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723488"
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a>Przewodnik: Szyfrowanie i odszyfrowywanie ciągów w Visual Basic
W tym instruktażu dowiesz się, jak używać <xref:System.Security.Cryptography.DESCryptoServiceProvider> klasy szyfrowanie i odszyfrowywanie ciągów za pomocą wersji dostawcy usług kryptograficznych Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algorytmu. Pierwszym krokiem jest utworzyć klasę otoki prostą, która hermetyzuje algorytmu 3DES i przechowuje zaszyfrowane dane jako ciąg zakodowany base-64. Następnie tej otoki służy do bezpiecznego przechowywania prywatnych danych użytkowników w pliku tekstowym dostępny publicznie.  
  
 Szyfrowanie można użyć do ochrony wpisu tajnego użytkownika (na przykład hasła) i poświadczeń nie można go odczytać przez nieautoryzowanych użytkowników. To jest ochrona tożsamości autoryzowanym użytkownikiem z skradzione, co chroni zasoby użytkownika i zapewnia uznawania. Szyfrowanie umożliwia również ochronę danych użytkownika przed dostępem nieautoryzowanych użytkowników.  
  
 Aby uzyskać więcej informacji, zobacz [usługi kryptograficzne](../../../../standard/security/cryptographic-services.md).  
  
> [!IMPORTANT]
>  Rijndael (teraz nazywana Advanced Encryption Standard [AES]) i algorytmy Triple Data Encryption Standard (3DES) zapewniają większe bezpieczeństwo niż DES, ponieważ są one więcej wymaga dużej mocy obliczeniowej. Aby uzyskać więcej informacji, zobacz <xref:System.Security.Cryptography.DES> i <xref:System.Security.Cryptography.Rijndael>.  
  
### <a name="to-create-the-encryption-wrapper"></a>Aby utworzyć otokę szyfrowania  
  
1.  Utwórz `Simple3Des` klasy do hermetyzacji metod szyfrowania i odszyfrowywania.  
  
     [!code-vb[VbVbalrStrings#38](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]  
  
2.  Dodaj import obszaru nazw kryptografii na początku pliku który zawiera `Simple3Des` klasy.  
  
     [!code-vb[VbVbalrStrings#77](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]  
  
3.  W `Simple3Des` klasy, Dodaj pole prywatne do przechowywania dostawcy usług kryptograficznych 3DES.  
  
     [!code-vb[VbVbalrStrings#39](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]  
  
4.  Dodaj metody prywatnej, która tworzy tablicę bajtów o określonej długości ze skrótu z określonym kluczem.  
  
     [!code-vb[VbVbalrStrings#41](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]  
  
5.  Dodaj Konstruktor do zainicjowania dostawcy usług kryptograficznych 3DES.  
  
     `key` Parametr określa `EncryptData` i `DecryptData` metody.  
  
     [!code-vb[VbVbalrStrings#40](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]  
  
6.  Dodaj metodę publiczną, która szyfruje ciągu.  
  
     [!code-vb[VbVbalrStrings#42](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]  
  
7.  Dodaj metodę publiczną, która odszyfrowuje ciągu.  
  
     [!code-vb[VbVbalrStrings#43](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]  
  
     Klasa otoki może teraz służyć do ochrony zasobów użytkownika. W tym przykładzie jest używany do bezpiecznego przechowywania prywatnych danych użytkowników w pliku tekstowym dostępny publicznie.  
  
### <a name="to-test-the-encryption-wrapper"></a>Aby przetestować otoki szyfrowania  
  
1.  W osobnej klasy, Dodaj metodę, która używa otoki `EncryptData` metodę, aby zaszyfrować ciągu i zapisz go do użytkownika w folderze Moje dokumenty.  
  
     [!code-vb[VbVbalrStrings#78](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]  
  
2.  Dodaj metodę, która odczytuje zaszyfrowany ciąg od użytkownika w folderze Moje dokumenty i odszyfrowuje ciągu z otoką `DecryptData` metody.  
  
     [!code-vb[VbVbalrStrings#79](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]  
  
3.  Dodaj kod interfejsu użytkownika, aby wywołać `TestEncoding` i `TestDecoding` metody.  
  
4.  Uruchom aplikację.  
  
     Podczas testowania aplikacji, zwróć uwagę, że jej nie powoduje odszyfrowania danych jeśli podano nieprawidłowe hasło.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Security.Cryptography>
- <xref:System.Security.Cryptography.DESCryptoServiceProvider>
- <xref:System.Security.Cryptography.DES>
- <xref:System.Security.Cryptography.TripleDES>
- <xref:System.Security.Cryptography.Rijndael>
- [Usługi kryptograficzne](../../../../standard/security/cryptographic-services.md)
