---
title: Model kryptografii programu .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography [.NET Framework], model
- encryption [.NET Framework], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7a60f03d85997d20b54366360f104519c9c75f5e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343873"
---
# <a name="net-framework-cryptography-model"></a>Model kryptografii programu .NET Framework
.NET Framework zawiera implementacje wiele standardowych algorytmów kryptograficznych. Algorytmy te są łatwe w użyciu i ma najbezpieczniejszą możliwe domyślne właściwości. Ponadto model kryptografii .NET Framework, dziedziczenie obiektu, projekt usługi stream i konfiguracji jest bardzo rozszerzalny.  
  
## <a name="object-inheritance"></a>Dziedziczenie obiektu  
 System zabezpieczeń .NET Framework implementuje extensible wzorzec dziedziczenia klas pochodnych. Hierarchia jest w następujący sposób:  
  
-   Typ algorytmu klasy takie jak <xref:System.Security.Cryptography.SymmetricAlgorithm>, <xref:System.Security.Cryptography.AsymmetricAlgorithm> lub <xref:System.Security.Cryptography.HashAlgorithm>. Ten poziom jest abstrakcyjna.  
  
-   Klasa algorytmu, który dziedziczy z klasy typu algorytmu; na przykład <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RC2>, lub <xref:System.Security.Cryptography.ECDiffieHellman>. Ten poziom jest abstrakcyjna.  
  
-   Implementacja klasy algorytmu, który dziedziczy z klasy algorytm; na przykład <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, lub <xref:System.Security.Cryptography.ECDiffieHellmanCng>. Ten poziom jest w pełni zaimplementowane.  
  
 Za pomocą tego wzorca klasy pochodne, jest łatwe do dodania, nowy algorytm lub nową metodę implementacji algorytm istniejących. Na przykład, aby utworzyć nowy algorytm klucza publicznego, użytkownik będzie dziedziczyć <xref:System.Security.Cryptography.AsymmetricAlgorithm> klasy. Aby utworzyć nową metodę implementacji określonego algorytmu, należy utworzyć klasę pochodną nieabstrakcyjnej tego algorytmu.  
  
## <a name="how-algorithms-are-implemented-in-the-net-framework"></a>Jak algorytmy są implementowane w programie .NET Framework  
 Jako przykład różne implementacje dostępne dla algorytmu należy wziąć pod uwagę algorytmów symetrycznych. Podstawa dla wszystkich algorytmów symetrycznych jest <xref:System.Security.Cryptography.SymmetricAlgorithm>, która jest dziedziczona przez następujących algorytmów:  
  
1. <xref:System.Security.Cryptography.Aes>  
  
2. <xref:System.Security.Cryptography.DES>  
  
3. <xref:System.Security.Cryptography.RC2>  
  
4. <xref:System.Security.Cryptography.Rijndael>  
  
5. <xref:System.Security.Cryptography.TripleDES>  
  
 <xref:System.Security.Cryptography.Aes> jest dziedziczona przez dwie klasy: <xref:System.Security.Cryptography.AesCryptoServiceProvider> i <xref:System.Security.Cryptography.AesManaged>. <xref:System.Security.Cryptography.AesCryptoServiceProvider> Klasy jest otokę wdrożenia Windows Cryptography API (CAPI) Aes, podczas gdy <xref:System.Security.Cryptography.AesManaged> klasy jest napisanych w całości w kodzie zarządzanym. Istnieje również trzeci typ implementacji Cryptography Next Generation (CNG), w dodatku do zarządzanych i CAPI implementacji. Na przykład algorytm CNG <xref:System.Security.Cryptography.ECDiffieHellmanCng>. Algorytmy CNG są dostępne w systemie Windows Vista i nowszych wersjach.  
  
 Możesz wybrać, która implementacja jest odpowiedni dla Ciebie.  Implementacje zarządzane są dostępne na wszystkich platformach, które obsługują .NET Framework.  Implementacje CAPI są dostępne w starszych systemach operacyjnych, a nie są już opracowywane są. CNG jest implementacją najnowsze, w której nowych wdrożeń będzie miała miejsce. Jednak implementacji zarządzanej nie zostały zatwierdzone przez przetwarzanie standardów FIPS (Federal Information) i może być wolniejsze niż klasy otoki.  
  
## <a name="stream-design"></a>Stream projektu  
 Środowisko uruchomieniowe języka wspólnego używa projektu zorientowane na strumień wykonania symetryczne algorytmy i algorytmów wyznaczania wartości skrótu. Podstawowe ten projekt jest <xref:System.Security.Cryptography.CryptoStream> klasy, która jest pochodną <xref:System.IO.Stream> klasy. Na podstawie Stream obiekty usług kryptograficznych obsługują interfejs jednego standardowego (`CryptoStream`) do obsługi transferu danych część obiektu. Ponieważ wszystkie obiekty są oparte na standardowych interfejsów, można połączyć w łańcuch jednocześnie wielu obiektów (takich jak obiektu skrótu, a następnie za pomocą obiektu szyfrowanie) i wykonywać wiele operacji na danych bez konieczności używania magazynu pośredniego dla niego. Modelu przesyłania strumieniowego umożliwia również tworzenie obiektów z mniejszych obiektów. Na przykład połączone algorytm szyfrowania i wyznaczania wartości skrótu można wyświetlać jako obiekt jednemu strumieniowi, chociaż ten obiekt może być kompilowany z zestawu obiektów strumienia.  
  
## <a name="cryptographic-configuration"></a>Konfiguracji kryptograficznej  
 Konfiguracji kryptograficznej pozwala rozpoznać określoną implementację algorytmu Nazwa algorytmu, umożliwiając rozszerzania klasy kryptografii platformy .NET Framework. Można dodać Twojej własnej implementacji sprzętowego lub programowego algorytmu i mapowania implementacja na Nazwa algorytmu wybranych przez użytkownika. Jeśli nie określono algorytmu w pliku konfiguracji, ustawienia domyślne są używane. Aby uzyskać więcej informacji na temat konfiguracji kryptograficznej zobacz [konfigurowanie klas kryptografii](../../../docs/framework/configure-apps/configure-cryptography-classes.md).  
  
## <a name="choosing-an-algorithm"></a>Wybieranie algorytmu  
 Możesz wybrać algorytm różnych powodów: na przykład integralność danych, ochrony prywatności danych lub do generowania klucza. Algorytmy Symmetric i wyznaczania wartości skrótu są przeznaczone do ochrony danych dla albo integralności (Ochrona zmiana) lub zachowania przyczyn (Ochrona z przeglądania). Algorytmy wyznaczania wartości skrótu są używane przede wszystkim dotyczące integralności danych.  
  
 Poniżej przedstawiono listę zalecanych algorytmów przez aplikację:  
  
-   Prywatność danych:  
  
    -   <xref:System.Security.Cryptography.Aes>  
  
-   Integralność danych:  
  
    -   <xref:System.Security.Cryptography.HMACSHA256>  
  
    -   <xref:System.Security.Cryptography.HMACSHA512>  
  
-   Podpis cyfrowy:  
  
    -   <xref:System.Security.Cryptography.ECDsa>  
  
    -   <xref:System.Security.Cryptography.RSA>  
  
-   Wymiana klucza:  
  
    -   <xref:System.Security.Cryptography.ECDiffieHellman>  
  
    -   <xref:System.Security.Cryptography.RSA>  
  
-   Generowanie liczby losowej:  
  
    -   <xref:System.Security.Cryptography.RNGCryptoServiceProvider>  
  
-   Generowanie klucza hasła:  
  
    -   <xref:System.Security.Cryptography.Rfc2898DeriveBytes>  
  
## <a name="see-also"></a>Zobacz także

- [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)
