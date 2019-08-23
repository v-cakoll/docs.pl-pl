---
title: Szyfrowanie i odszyfrowywanie ciągów w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: ee8691fedb537d1aa588eaac61624b445da64d1f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944429"
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a>Przewodnik: Szyfrowanie i odszyfrowywanie ciągów w Visual Basic
W tym instruktażu pokazano, jak używać <xref:System.Security.Cryptography.DESCryptoServiceProvider> klasy do szyfrowania i odszyfrowywania ciągów przy użyciu dostawcy usług kryptograficznych (CSP) algorytmu Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>). Pierwszym krokiem jest utworzenie prostej klasy otoki, która hermetyzuje algorytm 3DES i przechowuje zaszyfrowane dane jako ciąg zakodowany Base-64. Następnie ten otoka służy do bezpiecznego przechowywania prywatnych danych użytkownika w publicznie dostępnym pliku tekstowym.  
  
 Za pomocą szyfrowania można chronić klucze tajne użytkowników (na przykład hasła) i wprowadzać poświadczenia jako nieczytelne dla nieautoryzowanych użytkowników. Pozwala to chronić tożsamość autoryzowanego użytkownika przed kradzieżą, która chroni zasoby użytkownika i nie umożliwia wyparcia. Szyfrowanie umożliwia również ochronę danych użytkownika przed dostępem nieautoryzowanych użytkowników.  
  
 Aby uzyskać więcej informacji, zobacz [usługi kryptograficzne](../../../../standard/security/cryptographic-services.md).  
  
> [!IMPORTANT]
> Rijndael (teraz określane jako Advanced Encryption Standard [AES]) i algorytmy Triple Data Encryption Standard (3DES) zapewniają lepsze zabezpieczenia niż algorytm DES, ponieważ znacznie intensywnie korzystają z nich. Aby uzyskać więcej informacji, zobacz <xref:System.Security.Cryptography.DES> i <xref:System.Security.Cryptography.Rijndael>.  
  
### <a name="to-create-the-encryption-wrapper"></a>Aby utworzyć otokę szyfrowania  
  
1. `Simple3Des` Utwórz klasę, aby hermetyzować metody szyfrowania i odszyfrowywania.  
  
     [!code-vb[VbVbalrStrings#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#38)]  
  
2. Dodaj Import przestrzeni nazw kryptografii do początku pliku, który zawiera `Simple3Des` klasę.  
  
     [!code-vb[VbVbalrStrings#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#77)]  
  
3. `Simple3Des` W klasie Dodaj pole private, aby zachować dostawcę usług kryptograficznych 3DES.  
  
     [!code-vb[VbVbalrStrings#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#39)]  
  
4. Dodaj prywatną metodę, która tworzy tablicę bajtową o określonej długości ze skrótu określonego klucza.  
  
     [!code-vb[VbVbalrStrings#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#41)]  
  
5. Dodaj Konstruktor, aby zainicjować dostawcę usług kryptograficznych 3DES.  
  
     Parametr steruje metodami `DecryptData`i. `EncryptData` `key`  
  
     [!code-vb[VbVbalrStrings#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#40)]  
  
6. Dodaj metodę publiczną, która szyfruje ciąg.  
  
     [!code-vb[VbVbalrStrings#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#42)]  
  
7. Dodaj metodę publiczną, która odszyfrowuje ciąg.  
  
     [!code-vb[VbVbalrStrings#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#43)]  
  
     Klasy otoki można teraz używać do ochrony zasobów użytkownika. W tym przykładzie jest używany do bezpiecznego przechowywania prywatnych danych użytkownika w publicznie dostępnym pliku tekstowym.  
  
### <a name="to-test-the-encryption-wrapper"></a>Aby przetestować otokę szyfrowania  
  
1. W oddzielnym klasie Dodaj metodę, która używa `EncryptData` metody otoki, aby zaszyfrować ciąg i zapisać go w folderze Moje dokumenty użytkownika.  
  
     [!code-vb[VbVbalrStrings#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#78)]  
  
2. Dodaj metodę, która odczytuje zaszyfrowany ciąg z folderu Moje dokumenty użytkownika i odszyfrowuje ciąg za pomocą `DecryptData` metody otoki.  
  
     [!code-vb[VbVbalrStrings#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#79)]  
  
3. Dodaj kod interfejsu użytkownika, aby wywołać `TestEncoding` metody `TestDecoding` i.  
  
4. Uruchom aplikację.  
  
     Podczas testowania aplikacji należy zauważyć, że nie odszyfruje danych w przypadku podania nieprawidłowego hasła.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Cryptography>
- <xref:System.Security.Cryptography.DESCryptoServiceProvider>
- <xref:System.Security.Cryptography.DES>
- <xref:System.Security.Cryptography.TripleDES>
- <xref:System.Security.Cryptography.Rijndael>
- [Usługi kryptograficzne](../../../../standard/security/cryptographic-services.md)
