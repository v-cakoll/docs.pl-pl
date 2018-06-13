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
ms.openlocfilehash: ced7ed2cb8d3ae3bb24211c6e7dafd1744fb9559
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587459"
---
# <a name="net-framework-cryptography-model"></a>Model kryptografii programu .NET Framework
.NET Framework zapewnia implementacji wiele standardowych algorytmów kryptograficznych. Algorytmy te są łatwe w użyciu i mieć najbezpieczniejszy możliwe domyślnych właściwości. Ponadto model kryptografii .NET Framework dziedziczenia obiektu, strumienia projektowania i konfiguracji jest bardzo rozszerzonego.  
  
## <a name="object-inheritance"></a>Obiekt dziedziczenia  
 System zabezpieczeń .NET Framework implementuje extensible wzorzec dziedziczenia klas pochodnych. Hierarchia jest następujący:  
  
-   Typ algorytmu klasy, takich jak <xref:System.Security.Cryptography.SymmetricAlgorithm>, <xref:System.Security.Cryptography.AsymmetricAlgorithm> lub <xref:System.Security.Cryptography.HashAlgorithm>. Ten poziom jest abstrakcyjny.  
  
-   Klasa algorytmu, który dziedziczy z klasy typu algorytmu; na przykład <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RC2>, lub <xref:System.Security.Cryptography.ECDiffieHellman>. Ten poziom jest abstrakcyjny.  
  
-   Implementacja klasy algorytmu, który dziedziczy z klasy algorytm; na przykład <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, lub <xref:System.Security.Cryptography.ECDiffieHellmanCng>. Ten poziom pełni jest zaimplementowana.  
  
 Za pomocą tego wzorca klas pochodnych, jest łatwo dodać nowy algorytm lub nowej implementacji istniejących algorytmu. Na przykład aby utworzyć nowy algorytm klucza publicznego, użytkownik będzie dziedziczyć <xref:System.Security.Cryptography.AsymmetricAlgorithm> klasy. Aby utworzyć nową implementacją określonego algorytmu, należy utworzyć nieabstrakcyjnej klasy pochodnej z tego algorytmu.  
  
## <a name="how-algorithms-are-implemented-in-the-net-framework"></a>Jak algorytmy są implementowane w programie .NET Framework  
 Na przykład różnych implementacji dostępne dla algorytmu należy wziąć pod uwagę symetryczne algorytmy. Podstawowa dla wszystkich symetryczne algorytmy jest <xref:System.Security.Cryptography.SymmetricAlgorithm>, który jest dziedziczona przez następujących algorytmów:  
  
1.  <xref:System.Security.Cryptography.Aes>  
  
2.  <xref:System.Security.Cryptography.DES>  
  
3.  <xref:System.Security.Cryptography.RC2>  
  
4.  <xref:System.Security.Cryptography.Rijndael>  
  
5.  <xref:System.Security.Cryptography.TripleDES>  
  
 <xref:System.Security.Cryptography.Aes> jest dziedziczona przez dwie klasy: <xref:System.Security.Cryptography.AesCryptoServiceProvider> i <xref:System.Security.Cryptography.AesManaged>. <xref:System.Security.Cryptography.AesCryptoServiceProvider> Klasy jest otokę implementacji interfejsu API kryptografii systemu Windows (CAPI) Aes, podczas gdy <xref:System.Security.Cryptography.AesManaged> klasy są zapisywane w całości kodu zarządzanego. Istnieje również trzeci typ implementacji kryptografii nowej generacji (CNG), w implementacji CAPI i dodanie do zarządzanej. Przykładem jest algorytm CNG jest <xref:System.Security.Cryptography.ECDiffieHellmanCng>. Algorytmy CNG są dostępne w systemie Windows Vista lub nowszy.  
  
 Można wybrać, którego implementacja jest najlepsze dla Ciebie.  Implementacje zarządzane są dostępne na wszystkich platformach, które obsługuje programu .NET Framework.  Implementacje CAPI są dostępne w starszych systemach operacyjnych i są już tworzone. CNG jest implementacją najnowszych, gdzie nastąpi nowych wdrożeń. Jednak zarządzanych implementacji nie zostały zatwierdzone przez przetwarzanie standardami FIPS (Federal Information) i może być mniejsza niż klasy otoki.  
  
## <a name="stream-design"></a>Projekt strumienia  
 Środowisko uruchomieniowe języka wspólnego używa strumienia zorientowany wykonania symetryczne algorytmy i algorytmów wyznaczania wartości skrótu. Podstawowe ten projekt jest <xref:System.Security.Cryptography.CryptoStream> klasy, która jest pochodną <xref:System.IO.Stream> klasy. Na podstawie strumienia kryptograficznych obiekty obsługują interfejs pojedynczy standardowy (`CryptoStream`) do obsługi części transferu danych obiektu. Ponieważ wszystkie obiekty są tworzone na standardowy interfejs, użytkownik może łańcuch wielu obiektów (na przykład obiektu skrótu, a następnie za pomocą obiektu szyfrowania) i mogą wykonywać wiele operacji na danych, bez konieczności wszelkie pośrednie magazynu dla niego. Model przesyłania strumieniowego umożliwia również tworzenie obiektów z mniejszym obiektów. Na przykład łączna algorytmu szyfrowania i wyznaczania wartości skrótu można wyświetlać jako obiekt jednego strumienia, chociaż ten obiekt może być zbudowane z zestawu obiektów strumienia.  
  
## <a name="cryptographic-configuration"></a>Konfiguracja usług kryptograficznych  
 Konfiguracja kryptograficznych pozwala możesz rozwiązać określonej implementacji algorytm nazwę algorytmu, umożliwiając rozszerzalności klasy kryptografii platformy .NET Framework. Możesz dodać własnego sprzętu lub oprogramowania Implementacja algorytmu i mapowania implementacji nazwę algorytmu wybranych przez użytkownika. Jeśli w pliku konfiguracji nie określono algorytmu, używane są ustawienia domyślne. Aby uzyskać więcej informacji na temat konfiguracji kryptograficznych, zobacz [Konfigurowanie klasy kryptografii](../../../docs/framework/configure-apps/configure-cryptography-classes.md).  
  
## <a name="choosing-an-algorithm"></a>Wybieranie algorytmu  
 Można wybrać algorytm różnych powodów: na przykład w przypadku integralność danych, poufność danych, lub aby wygenerować klucz. Algorytmy Symmetric i wyznaczania wartości skrótu są przeznaczone do ochrony danych albo integralności (Ochrona z zmian) lub prywatności przyczyn (Ochrona z wyświetlanie). Algorytmy wyznaczania wartości skrótu są używane głównie w celu zapewnienia integralności danych.  
  
 Poniżej przedstawiono listę zalecanych algorytmów przez aplikację:  
  
-   Prywatność danych:  
  
    -   <xref:System.Security.Cryptography.Aes>  
  
-   Integralność danych:  
  
    -   <xref:System.Security.Cryptography.HMACSHA256>  
  
    -   <xref:System.Security.Cryptography.HMACSHA512>  
  
-   Podpis cyfrowy:  
  
    -   <xref:System.Security.Cryptography.ECDsa>  
  
    -   <xref:System.Security.Cryptography.RSA>  
  
-   Wymiana kluczy:  
  
    -   <xref:System.Security.Cryptography.ECDiffieHellman>  
  
    -   <xref:System.Security.Cryptography.RSA>  
  
-   Generowanie liczby losowej:  
  
    -   <xref:System.Security.Cryptography.RNGCryptoServiceProvider>  
  
-   Generowanie klucza z hasła:  
  
    -   <xref:System.Security.Cryptography.Rfc2898DeriveBytes>  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)  
 
