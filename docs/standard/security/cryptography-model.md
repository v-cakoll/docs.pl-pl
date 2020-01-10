---
title: Model kryptografii programu .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography [.NET Framework], model
- encryption [.NET Framework], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
ms.openlocfilehash: f0c00e4cc866c537fe26dd1ad466d6cde95bc608
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706230"
---
# <a name="net-framework-cryptography-model"></a>Model kryptografii programu .NET Framework

.NET Framework udostępnia implementacje wielu standardowych algorytmów kryptograficznych. Te algorytmy są łatwe w użyciu i mają najbezpieczniejsze możliwe właściwości domyślne. Dodatkowo rozszerzalny model dziedziczenia obiektów, projektu i konfiguracji .NET Framework

## <a name="object-inheritance"></a>Dziedziczenie obiektu

System zabezpieczeń .NET Framework implementuje rozszerzalny wzorzec dziedziczenia klasy pochodnej. Hierarchia jest następująca:

- Klasa typu algorytmu, taka jak <xref:System.Security.Cryptography.SymmetricAlgorithm>, <xref:System.Security.Cryptography.AsymmetricAlgorithm> lub <xref:System.Security.Cryptography.HashAlgorithm>. Ten poziom jest abstrakcyjny.

- Klasa algorytmu, która dziedziczy z klasy typu algorytmu; na przykład <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RC2>lub <xref:System.Security.Cryptography.ECDiffieHellman>. Ten poziom jest abstrakcyjny.

- Implementacja klasy algorytmu, która dziedziczy z klasy algorytmu; na przykład <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>lub <xref:System.Security.Cryptography.ECDiffieHellmanCng>. Ten poziom jest w pełni zaimplementowany.

Korzystając z tego wzorca klas pochodnych, można łatwo dodać nowy algorytm lub nową implementację istniejącego algorytmu. Na przykład, aby utworzyć nowy algorytm klucza publicznego, można dziedziczyć z klasy <xref:System.Security.Cryptography.AsymmetricAlgorithm>. Aby utworzyć nową implementację określonego algorytmu, należy utworzyć nieabstrakcyjną klasę pochodną tego algorytmu.

## <a name="how-algorithms-are-implemented-in-the-net-framework"></a>Jak zaimplementowane są algorytmy w .NET Framework

Przykładem różnych implementacji dla algorytmu, należy wziąć pod uwagę Algorytmy symetryczne. Podstawą dla wszystkich algorytmów symetrycznych jest <xref:System.Security.Cryptography.SymmetricAlgorithm>, która jest dziedziczona przez następujące algorytmy:

1. <xref:System.Security.Cryptography.Aes>

2. <xref:System.Security.Cryptography.DES>

3. <xref:System.Security.Cryptography.RC2>

4. <xref:System.Security.Cryptography.Rijndael>

5. <xref:System.Security.Cryptography.TripleDES>

<xref:System.Security.Cryptography.Aes> jest dziedziczona przez dwie klasy: <xref:System.Security.Cryptography.AesCryptoServiceProvider> i <xref:System.Security.Cryptography.AesManaged>. Klasa <xref:System.Security.Cryptography.AesCryptoServiceProvider> to otoka z implementacją algorytmu AES (Windows Cryptography API), natomiast Klasa <xref:System.Security.Cryptography.AesManaged> jest zapisywana w całości w kodzie zarządzanym. Oprócz implementacji zarządzanych i CAPI istnieje również trzeci typ implementacji, Kryptografia nowej generacji (CNG). Przykładem algorytmu CNG jest <xref:System.Security.Cryptography.ECDiffieHellmanCng>. Algorytmy CNG są dostępne w systemie Windows Vista i nowszych.

Możesz wybrać, która implementacja jest dla Ciebie najlepsza.  Zarządzane wdrożenia są dostępne na wszystkich platformach, które obsługują .NET Framework.  Implementacje CAPI są dostępne w starszych systemach operacyjnych i nie są już opracowywane. CNG to bardzo Najnowsza implementacja, w której nastąpi nowe programowanie. Jednak implementacje zarządzane nie są certyfikowane przez standardy FIPS (Federal Information Processing Standards) i mogą być wolniejsze niż klasy otoki.

## <a name="stream-design"></a>Projekt strumienia

Środowisko uruchomieniowe języka wspólnego używa projektu zorientowanego na strumień do implementowania algorytmów symetrycznych i algorytmów wyznaczania wartości skrótu. Rdzeń tego projektu jest klasą <xref:System.Security.Cryptography.CryptoStream>, która pochodzi od klasy <xref:System.IO.Stream>. Obiekty kryptograficzne oparte na strumieniach obsługują pojedynczy standardowy interfejs (`CryptoStream`) do obsługi częściowego transferu danych obiektu. Ze względu na to, że wszystkie obiekty są oparte na standardowym interfejsie, można połączyć wiele obiektów (takich jak obiekt skrótu, po którym następuje obiekt szyfrowania) i można wykonać wiele operacji na danych bez potrzeby przechowywania pośredniego. Model przesyłania strumieniowego umożliwia również Kompilowanie obiektów z mniejszych obiektów. Na przykład połączone szyfrowanie i algorytm wyznaczania wartości skrótu można wyświetlić jako obiekt pojedynczego strumienia, chociaż ten obiekt może być skompilowany na podstawie zestawu obiektów strumienia.

## <a name="cryptographic-configuration"></a>Konfiguracja kryptograficzna

Konfiguracja kryptograficzna pozwala rozpoznać określoną implementację algorytmu do nazwy algorytmu, co pozwala na rozszerzanie klas kryptografii .NET Framework. Możesz dodać własną implementację sprzętu lub oprogramowania do algorytmu i zmapować implementację do wybranej nazwy algorytmu. Jeśli w pliku konfiguracji nie określono algorytmu, zostaną użyte ustawienia domyślne. Aby uzyskać więcej informacji na temat konfiguracji kryptograficznej, zobacz [Konfigurowanie klas kryptograficznych](../../../docs/framework/configure-apps/configure-cryptography-classes.md).

## <a name="choosing-an-algorithm"></a>Wybieranie algorytmu

Istnieje możliwość wybrania algorytmu z różnych przyczyn: na przykład w celu zapewnienia integralności danych lub wygenerowania klucza. Algorytmy symetryczne i hash są przeznaczone do ochrony danych z powodów związanych z integralnością (ochrona przed zmianami) lub z przyczyn zachowania poufności informacji (ochrona przed wyświetlaniem). Algorytmy wyznaczania wartości skrótu są używane głównie w celu zapewnienia integralności danych.

Poniżej znajduje się lista zalecanych algorytmów według aplikacji:

- Prywatność danych:

  - <xref:System.Security.Cryptography.Aes>

- Integralność danych:

  - <xref:System.Security.Cryptography.HMACSHA256>

  - <xref:System.Security.Cryptography.HMACSHA512>

- Podpis cyfrowy:

  - <xref:System.Security.Cryptography.ECDsa>

  - <xref:System.Security.Cryptography.RSA>

- Wymiana kluczy:

  - <xref:System.Security.Cryptography.ECDiffieHellman>

  - <xref:System.Security.Cryptography.RSA>

- Generowanie liczb losowych:

  - <xref:System.Security.Cryptography.RNGCryptoServiceProvider>

- Generowanie klucza przy użyciu hasła:

  - <xref:System.Security.Cryptography.Rfc2898DeriveBytes>

## <a name="see-also"></a>Zobacz także

- [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)
