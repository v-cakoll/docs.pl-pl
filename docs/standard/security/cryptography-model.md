---
title: Model kryptografii programu .NET Framework
description: Przejrzyj implementacje zwykłych algorytmów kryptograficznych w programie .NET. Zapoznaj się z rozszerzalnym modelem kryptografii dziedziczenia obiektów, projektem strumienia i konfiguracją &.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography [.NET Framework], model
- encryption [.NET Framework], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
ms.openlocfilehash: 11af4c15c8b291df898a3c2416faa15875eab70b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596322"
---
# <a name="net-framework-cryptography-model"></a>Model kryptografii programu .NET Framework

.NET Framework udostępnia implementacje wielu standardowych algorytmów kryptograficznych. Te algorytmy są łatwe w użyciu i mają najbezpieczniejsze możliwe właściwości domyślne. Dodatkowo rozszerzalny model dziedziczenia obiektów, projektu i konfiguracji .NET Framework

## <a name="object-inheritance"></a>Dziedziczenie obiektu

System zabezpieczeń .NET Framework implementuje rozszerzalny wzorzec dziedziczenia klasy pochodnej. Hierarchia jest następująca:

- Klasa typu algorytmu, taka jak <xref:System.Security.Cryptography.SymmetricAlgorithm> , <xref:System.Security.Cryptography.AsymmetricAlgorithm> lub <xref:System.Security.Cryptography.HashAlgorithm> . Ten poziom jest abstrakcyjny.

- Klasa algorytmu, która dziedziczy z klasy typu algorytmu; na przykład, <xref:System.Security.Cryptography.Aes> , <xref:System.Security.Cryptography.RC2> lub <xref:System.Security.Cryptography.ECDiffieHellman> . Ten poziom jest abstrakcyjny.

- Implementacja klasy algorytmu, która dziedziczy z klasy algorytmu; na przykład, <xref:System.Security.Cryptography.AesManaged> , <xref:System.Security.Cryptography.RC2CryptoServiceProvider> lub <xref:System.Security.Cryptography.ECDiffieHellmanCng> . Ten poziom jest w pełni zaimplementowany.

Korzystając z tego wzorca klas pochodnych, można łatwo dodać nowy algorytm lub nową implementację istniejącego algorytmu. Na przykład, aby utworzyć nowy algorytm klucza publicznego, można dziedziczyć z <xref:System.Security.Cryptography.AsymmetricAlgorithm> klasy. Aby utworzyć nową implementację określonego algorytmu, należy utworzyć nieabstrakcyjną klasę pochodną tego algorytmu.

## <a name="how-algorithms-are-implemented-in-the-net-framework"></a>Jak zaimplementowane są algorytmy w .NET Framework

Przykładem różnych implementacji dla algorytmu, należy wziąć pod uwagę Algorytmy symetryczne. Podstawowa dla wszystkich algorytmów symetrycznych jest <xref:System.Security.Cryptography.SymmetricAlgorithm> dziedziczona przez następujące algorytmy:

* <xref:System.Security.Cryptography.Aes>
* <xref:System.Security.Cryptography.DES>
* <xref:System.Security.Cryptography.RC2>
* <xref:System.Security.Cryptography.Rijndael>
* <xref:System.Security.Cryptography.TripleDES>

<xref:System.Security.Cryptography.Aes>jest dziedziczona przez dwie klasy: <xref:System.Security.Cryptography.AesCryptoServiceProvider> i <xref:System.Security.Cryptography.AesManaged> . <xref:System.Security.Cryptography.AesCryptoServiceProvider>Klasa jest otoką opartą na implementacji AES interfejsu API (CAPI) systemu Windows, podczas gdy <xref:System.Security.Cryptography.AesManaged> Klasa jest zapisywana w całości w kodzie zarządzanym. Oprócz implementacji zarządzanych i CAPI istnieje również trzeci typ implementacji, Kryptografia nowej generacji (CNG). Przykładem algorytmu CNG jest <xref:System.Security.Cryptography.ECDiffieHellmanCng> . Algorytmy CNG są dostępne w systemie Windows Vista i nowszych.

Możesz wybrać, która implementacja jest dla Ciebie najlepsza. Zarządzane wdrożenia są dostępne na wszystkich platformach, które obsługują .NET Framework. Implementacje CAPI są dostępne w starszych systemach operacyjnych i nie są już opracowywane. CNG to najnowsza implementacja, w której nastąpi nowe programowanie. Jednak implementacje zarządzane nie są certyfikowane przez standardy FIPS (Federal Information Processing Standards) i mogą być wolniejsze niż klasy otoki.

## <a name="stream-design"></a>Projekt strumienia

Środowisko uruchomieniowe języka wspólnego używa projektu zorientowanego na strumień do implementowania algorytmów symetrycznych i algorytmów wyznaczania wartości skrótu. Rdzeń tego projektu jest <xref:System.Security.Cryptography.CryptoStream> klasą, która pochodzi od <xref:System.IO.Stream> klasy. Obiekty kryptograficzne oparte na strumieniach obsługują pojedynczy standardowy interfejs ( `CryptoStream` ) do obsługi częściowego transferu danych obiektu. Ze względu na to, że wszystkie obiekty są oparte na standardowym interfejsie, można połączyć wiele obiektów (takich jak obiekt skrótu, po którym następuje obiekt szyfrowania) i można wykonać wiele operacji na danych bez potrzeby przechowywania pośredniego. Model przesyłania strumieniowego umożliwia również Kompilowanie obiektów z mniejszych obiektów. Na przykład połączone szyfrowanie i algorytm wyznaczania wartości skrótu można wyświetlić jako obiekt pojedynczego strumienia, chociaż ten obiekt może być skompilowany na podstawie zestawu obiektów strumienia.

## <a name="cryptographic-configuration"></a>Konfiguracja kryptograficzna

Konfiguracja kryptograficzna pozwala rozpoznać określoną implementację algorytmu do nazwy algorytmu, co pozwala na rozszerzanie klas kryptografii .NET Framework. Możesz dodać własną implementację sprzętu lub oprogramowania do algorytmu i zmapować implementację do wybranej nazwy algorytmu. Jeśli w pliku konfiguracji nie określono algorytmu, zostaną użyte ustawienia domyślne. Aby uzyskać więcej informacji na temat konfiguracji kryptograficznej, zobacz [Konfigurowanie klas kryptograficznych](../../framework/configure-apps/configure-cryptography-classes.md).

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

## <a name="see-also"></a>Zobacz też

- [Usługi kryptograficzne](cryptographic-services.md)
- [Zastosowano protokoły kryptografii, algorytmy i kod źródłowy w C, przez Bruce Schneier](https://www.schneier.com/books/applied_cryptography/)
