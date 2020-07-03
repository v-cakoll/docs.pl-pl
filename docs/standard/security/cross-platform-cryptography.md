---
title: Kryptografia międzyplatformowa w oprogramowaniu .NET Core i .NET 5
description: Informacje o możliwościach kryptograficznych na platformach obsługiwanych przez platformę .NET.
ms.date: 06/19/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography, cross-platform
- encryption, cross-platform
ms.openlocfilehash: 793a9bc55e5bd660374abd2ae81899e63ce3f36a
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85854015"
---
# <a name="cross-platform-cryptography-in-net-core-and-net-5"></a>Kryptografia międzyplatformowa w oprogramowaniu .NET Core i .NET 5

Operacje kryptograficzne w oprogramowaniu .NET Core i .NET 5 są wykonywane przez biblioteki systemu operacyjnego. Ta zależność ma zalety:

* Aplikacje .NET korzystają z niezawodności systemu operacyjnego. Bezpieczne przechowywanie bibliotek kryptograficznych przez luki w zabezpieczeniach jest wysokim priorytetem dla dostawców systemu operacyjnego. W tym celu dostarczają aktualizacje, które powinny być stosowane przez administratorów systemu.
* Aplikacje .NET mają dostęp do algorytmów zweryfikowanych przez FIPS, jeśli biblioteki systemu operacyjnego są zweryfikowane w trybie FIPS.

Zależność od bibliotek systemu operacyjnego oznacza również, że aplikacje .NET mogą korzystać tylko z funkcji kryptograficznych obsługiwanych przez system operacyjny. Wszystkie platformy obsługują pewne podstawowe funkcje, ale niektóre funkcje obsługiwane przez platformę .NET nie mogą być używane na niektórych platformach. W tym artykule opisano funkcje, które są obsługiwane na każdej platformie.

W tym artykule przyjęto założenie, że masz praktyczną wiedzę na temat kryptografii w programie .NET. Aby uzyskać więcej informacji, zobacz [model kryptografii .NET](cryptography-model.md) i [usług kryptograficznych platformy .NET](cryptographic-services.md).

## <a name="hash-algorithms"></a>Algorytmy skrótu

Wszystkie klasy algorytmu wyznaczania wartości skrótu i uwierzytelniania komunikatów oparte na skrótach (HMAC), w tym `*Managed` klasy, przełożyć na biblioteki systemu operacyjnego. Chociaż różne biblioteki systemu operacyjnego różnią się od wydajności, powinny być zgodne.

## <a name="symmetric-encryption"></a>Szyfrowanie symetryczne

Podstawowe szyfry i łańcuchy są wykonywane przez biblioteki systemowe, a wszystkie są obsługiwane przez wszystkie platformy.

| Szyfrowanie + tryb | Windows | Linux | macOS |
|---------------|---------|-------|-------|
| AES — CBC       | ✔️     | ✔️    | ✔️   |
| AES — EBC       | ✔️     | ✔️    | ✔️   |
| ALGORYTM 3DES-CBC      | ✔️     | ✔️    | ✔️   |
| 3DES — EBC      | ✔️     | ✔️    | ✔️   |
| DES — CBC       | ✔️     | ✔️    | ✔️   |
| DES — EBC       | ✔️     | ✔️    | ✔️   |

## <a name="authenticated-encryption"></a>Uwierzytelnione szyfrowanie

Obsługa szyfrowania uwierzytelnionego (AE) jest dostępna dla algorytmów AES-CCM i AES-GCM za pośrednictwem <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName> <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName> klas i.

W systemach Windows i Linux implementacje AES-CCM i AES-GCM są udostępniane przez biblioteki systemu operacyjnego.

### <a name="aes-ccm-and-aes-gcm-on-macos"></a>AES-CCM i AES-GCM na macOS

W systemie macOS biblioteki systemowe nie obsługują AES-CCM ani AES-GCM dla kodu innych firm, więc <xref:System.Security.Cryptography.AesCcm> <xref:System.Security.Cryptography.AesGcm> klasy i używają OpenSSL do obsługi. Użytkownicy na macOS muszą uzyskać odpowiednią kopię OpenSSL (libcrypto) dla tych typów, aby działała, i musi znajdować się w ścieżce, z której system będzie domyślnie ładować bibliotekę. Zalecamy zainstalowanie OpenSSL z Menedżera pakietów, takiego jak oprogramowania homebrew.

`libcrypto.0.9.7.dylib`Biblioteki i `libcrypto.0.9.8.dylib` zawarte w macOS pochodzą z wcześniejszych wersji OpenSSL i nie będą używane. `libcrypto.35.dylib`Biblioteki, `libcrypto.41.dylib` i `libcrypto.42.dylib` są z LibreSSL i nie będą używane.

### <a name="aes-ccm-keys-nonces-and-tags"></a>AES-klucze CCM, identyfikatorów jednorazowych i Tagi

* Rozmiary kluczy

  AES-CCM działa z kluczami 128, 192 i 256-bitowymi.

* Rozmiary nonce

  <xref:System.Security.Cryptography.AesCcm>Klasa obsługuje 56, 64, 72, 80, 88, 96 i 104-bit (7, 8, 9, 10, 11, 12 i 13-bajtowe) identyfikatorów jednorazowych.

* Rozmiary tagów

  <xref:System.Security.Cryptography.AesCcm>Klasa obsługuje tworzenie lub przetwarzanie 32, 48, 64, 80, 96, 112 i 128-bit (4, 8, 10, 12, 14 i 16-bajtowych) tagów.

### <a name="aes-gcm-keys-nonces-and-tags"></a>AES-GCM klucze, identyfikatorów jednorazowych i Tagi

* Rozmiary kluczy

  Algorytm AES-GCM współpracuje z kluczami 128, 192 i 256-bitowymi.

* Rozmiary nonce

  <xref:System.Security.Cryptography.AesGcm>Klasa obsługuje tylko 96-bitowe (12-bajtowe) identyfikatorów jednorazowych.

* Rozmiary tagów

  <xref:System.Security.Cryptography.AesGcm>Klasa obsługuje tworzenie lub przetwarzanie 96, 104, 112, 120 i 128-bit (12, 13, 14, 15 i 16-bajtowych) tagów.

## <a name="asymmetric-cryptography"></a>Kryptografia asymetryczne

Ta sekcja zawiera następujące podsekcje:

* [RSA](#rsa)
* [ECDSA](#ecdsa)
* [ECDH](#ecdh)
* [DSA](#dsa)

### <a name="rsa"></a>RSA

Generowanie kluczy RSA (Rivest – Shamir – Adleman) jest wykonywane przez biblioteki systemu operacyjnego i podlegają ograniczeniom rozmiaru i charakterystyce wydajności.

Operacje na klucz RSA są wykonywane przez biblioteki systemu operacyjnego, a typy kluczy, które mogą być ładowane, podlegają wymaganiom systemu operacyjnego.

Platforma .NET nie ujawnia "nieprzetworzonych" (nieuzupełnionych) operacji RSA.

Biblioteki systemu operacyjnego są używane do szyfrowania i uzupełniania odszyfrowywania. Nie wszystkie platformy obsługują te same opcje uzupełniania:

| Tryb uzupełniania                          | Windows (CNG) | Linux (OpenSSL) | macOS | Windows (CAPI) |
|---------------------------------------|---------------|-----------------|-------|----------------|
| Szyfrowanie PKCS1                      | ✔️           | ✔️              | ✔️   | ✔️             |
| OAEP — SHA-1                          | ✔️           | ✔️              | ✔️   | ✔️             |
| OAEP-SHA-2 (SHA256, SHA384, SHA512) | ✔️           | ✔️              | ✔️   | ❌             |
| Sygnatura PKCS1 (MD5, SHA-1)          | ✔️           | ✔️              | ✔️   | ✔️             |
| Sygnatura PKCS1 (SHA-2)               | ✔️           | ✔️              | ✔️   | ⚠️\*           |
| PSS                                   | ✔️           | ✔️              | ✔️   | ❌             |

\*Interfejs CryptoAPI systemu Windows (CAPI) jest w stanie PKCS1 podpis z algorytmem SHA-2. Jednak pojedynczy obiekt RSA może zostać załadowany przez dostawcę usług kryptograficznych (CSP), który go nie obsługuje.

#### <a name="rsa-on-windows"></a>RSA w systemie Windows

* Interfejs Windows CryptoAPI (CAPI) jest używany zawsze, gdy [`new RSACryptoServiceProvider()`](xref:System.Security.Cryptography.RSACryptoServiceProvider) jest używany.
* Użycie usługi Windows Cryptography API Next Generation (CNG) jest używane za każdym razem, gdy [`new RSACng()`](xref:System.Security.Cryptography.RSACng) jest używany.
* Obiekt zwrócony przez <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> jest wewnętrznie obsługiwany przez CNG systemu Windows. Korzystanie z systemu Windows CNG jest szczegółami implementacji i może ulec zmianie.
* <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A>Metoda rozszerzająca dla <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> zwraca <xref:System.Security.Cryptography.RSACng> wystąpienia. To użycie <xref:System.Security.Cryptography.RSACng> jest szczegółami implementacji i może ulec zmianie.
* <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A>Metoda rozszerzenia dla <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> obecnie preferuje <xref:System.Security.Cryptography.RSACng> wystąpienie, ale jeśli <xref:System.Security.Cryptography.RSACng> nie można otworzyć klucza, <xref:System.Security.Cryptography.RSACryptoServiceProvider> zostanie podjęta próba. Preferowany dostawca jest szczegółami implementacji i może ulec zmianie.

#### <a name="rsa-native-interop"></a>Natywna międzyoperacyjność RSA

Platforma .NET udostępnia typy umożliwiające współdziałanie programów z bibliotekami systemu operacyjnego, które są używane przez kod kryptografii platformy .NET. Typy, które nie są tłumaczone między platformami i powinny być używane tylko wtedy, gdy jest to konieczne.

| Typ                                                         | Windows | Linux         | macOS         |
|--------------------------------------------------------------|---------|---------------|---------------|
| <xref:System.Security.Cryptography.RSACryptoServiceProvider> | ✔️     | ⚠️<sup>jedno</sup>| ⚠️<sup>jedno</sup> |
| <xref:System.Security.Cryptography.RSACng>                   | ✔️     | ❌            | ❌            |
| <xref:System.Security.Cryptography.RSAOpenSsl>               | ❌     | ✔️            | ⚠️<sup>dwóch</sup> |

<sup>1</sup> w systemach MacOS i Linux <xref:System.Security.Cryptography.RSACryptoServiceProvider> można używać w celu zapewnienia zgodności z istniejącymi programami. W takim przypadku każda metoda wymagająca międzyoperacyjności systemu operacyjnego, taka jak otwieranie klucza nazwanego, zgłasza <xref:System.PlatformNotSupportedException> .

<sup>2</sup> w macOS, <xref:System.Security.Cryptography.RSAOpenSsl> działa, jeśli zainstalowano OpenSSL i odpowiednie DYLIB libcrypto można znaleźć za pośrednictwem ładowania biblioteki dynamicznej. Jeśli nie można znaleźć odpowiedniej biblioteki, zostaną zgłoszone wyjątki.

### <a name="ecdsa"></a>ECDSA

Generowanie klucza ECDSA (algorytmu cyfrowego krzywej eliptyczna) jest wykonywane przez biblioteki systemu operacyjnego i podlega ograniczeniom rozmiaru i charakterystyce wydajności.

Krzywe klucza ECDSA są definiowane przez biblioteki systemu operacyjnego i podlegają ich ograniczeniom.

| Krzywa eliptyczna                     | Windows 10    | Windows 7 — 8,1 | Linux         | macOS         |
|------------------------------------|---------------|-----------------|---------------|---------------|
| NIST P-256 (secp256r1)             | ✔️           | ✔️              | ✔️           | ✔️            |
| NIST P-384 (secp384r1)             | ✔️           | ✔️              | ✔️           | ✔️            |
| NIST P-521 (secp521r1)             | ✔️           | ✔️              | ✔️           | ✔️            |
| Krzywe Brainpool (jako nazwane krzywe) | ✔️           | ❌              | ⚠️<sup>jedno</sup>| ❌           |
| Inne nazwane krzywe                 | ⚠️<sup>dwóch</sup>| ❌             | ⚠️<sup>jedno</sup>| ❌           |
| Jawne krzywe                    | ✔️           | ❌              | ✔️           | ❌            |
| Eksportuj lub Importuj jako jawne       | ✔️           | ❌<sup>r.3</sup>  | ✔️           | ❌<sup>r.3</sup>|

<sup>1</sup> dystrybucje systemu Linux nie wszystkie obsługują te same nazwane krzywe.

<sup>2</sup> obsługa nazwanych krzywych została dodana do systemu Windows CNG w systemie Windows 10. Aby uzyskać więcej informacji, zobacz [CNG o nazwie krzywe eliptyczna](https://msdn.microsoft.com/library/windows/desktop/mt632245(v=vs.85).aspx). Nazwane krzywe nie są dostępne we wcześniejszych wersjach systemu Windows, z wyjątkiem trzech krzywych w systemie Windows 7.

<sup>3</sup> Eksportowanie z jawnymi parametrami krzywej wymaga obsługi biblioteki systemu operacyjnego, która nie jest dostępna w macOS i starszych wersjach systemu Windows.

#### <a name="ecdsa-native-interop"></a>Natywna międzyoperacyjna ECDSA

Platforma .NET udostępnia typy umożliwiające współdziałanie programów z bibliotekami systemu operacyjnego, które są używane przez kod kryptografii platformy .NET. Typy, których to dotyczy, nie są tłumaczone między platformami i powinny być bezpośrednio używane tylko wtedy, gdy jest to konieczne.

| Typ                                             | Windows | Linux | macOS |
|--------------------------------------------------|---------|-------|-------|
| <xref:System.Security.Cryptography.ECDsaCng>     | ✔️     | ❌    | ❌    |
| <xref:System.Security.Cryptography.ECDsaOpenSsl> | ❌     | ✔️    | ⚠️\*  |

\*W systemie macOS <xref:System.Security.Cryptography.ECDsaOpenSsl> działa, jeśli OpenSSL jest zainstalowany w systemie i odpowiednie DYLIB libcrypto można znaleźć za pośrednictwem ładowania biblioteki dynamicznej. Jeśli nie można znaleźć odpowiedniej biblioteki, zostaną zgłoszone wyjątki.

### <a name="ecdh"></a>ECDH

Generowanie kluczy ECDH (krzywej eliptyczna Diffie-Hellmana) jest wykonywane przez biblioteki systemu operacyjnego i podlegają ograniczeniom rozmiaru i charakterystyce wydajności.

<xref:System.Security.Cryptography.ECDiffieHellman>Klasa nie zwraca wartości "RAW" obliczeń ECDH. Wszystkie zwrócone dane są w zakresie podstawowych funkcji wyprowadzania:

* WARTOŚĆ SKRÓTU (Z)
* HASH (poprzedź | | Z | | łączono
* HMAC (Key, Z)
* HMAC (klawisz, poprzedź | | Z | | łączono
* HMAC (Z, Z)
* HMAC (Z, poprzedź | | Z | | łączono
* Tls11Prf (etykieta, inicjator)

Krzywe klucza ECDH są definiowane przez biblioteki systemu operacyjnego i podlegają ich ograniczeniom.

| Krzywa eliptyczna                     | Windows 10    | Windows 7 — 8,1 | Linux         | macOS         |
|------------------------------------|---------------|-----------------|---------------|---------------|
| NIST P-256 (secp256r1)             | ✔️           | ✔️              | ✔️           | ✔️            |
| NIST P-384 (secp384r1)             | ✔️           | ✔️              | ✔️           | ✔️            |
| NIST P-521 (secp521r1)             | ✔️           | ✔️              | ✔️           | ✔️            |
| Krzywe Brainpool (jako nazwane krzywe) | ✔️           | ❌              | ⚠️<sup>jedno</sup>| ❌           |
| inne nazwane krzywe                 | ⚠️<sup>dwóch</sup>| ❌             | ⚠️<sup>jedno</sup>| ❌           |
| jawne krzywe                    | ✔️           | ❌              | ✔️           | ❌            |
| Eksportuj lub Importuj jako jawne       | ✔️           | ❌<sup>r.3</sup>  | ✔️           | ❌<sup>r.3</sup>|

<sup>1</sup> dystrybucje systemu Linux nie wszystkie obsługują te same nazwane krzywe.

<sup>2</sup> obsługa nazwanych krzywych została dodana do systemu Windows CNG w systemie Windows 10. Aby uzyskać więcej informacji, zobacz [CNG o nazwie krzywe eliptyczna](https://msdn.microsoft.com/library/windows/desktop/mt632245(v=vs.85).aspx). Nazwane krzywe nie są dostępne we wcześniejszych wersjach systemu Windows, z wyjątkiem trzech krzywych w systemie Windows 7.

<sup>3</sup> Eksportowanie z jawnymi parametrami krzywej wymaga obsługi biblioteki systemu operacyjnego, która nie jest dostępna w macOS i starszych wersjach systemu Windows.

#### <a name="ecdh-native-interop"></a>Natywna międzyoperacyjna ECDH

Platforma .NET udostępnia typy umożliwiające współdziałanie programów z bibliotekami systemu operacyjnego, które są używane przez platformę .NET. Typy, których to dotyczy, nie są tłumaczone między platformami i powinny być bezpośrednio używane tylko wtedy, gdy jest to konieczne.

| Typ                                                       | Windows | Linux | macOS |
|------------------------------------------------------------|---------|-------|-------|
| <xref:System.Security.Cryptography.ECDiffieHellmanCng>     | ✔️     | ❌    | ❌   |
| <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> | ❌     | ✔️    | ⚠️\* |

\*Na macOS, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> działa, jeśli zainstalowano OpenSSL i odpowiednie DYLIB libcrypto można znaleźć za pośrednictwem ładowania biblioteki dynamicznej. Jeśli nie można znaleźć odpowiedniej biblioteki, zostaną zgłoszone wyjątki.

### <a name="dsa"></a>DSA

Proces DSA (algorytm podpisu cyfrowego) jest wykonywany przez biblioteki systemowe i podlega ograniczeniom rozmiaru i charakterystyce wydajności.

| Funkcja                      | Windows CNG | Linux | macOS         | Windows CAPI |
|-------------------------------|-------------|-------|---------------|--------------|
| Tworzenie klucza (<= 1024 bitów)   | ✔️         | ✔️    | ❌            | ✔️           |
| Tworzenie klucza (> 1024 bitów)    | ✔️         | ✔️    | ❌            | ❌            |
| Ładowanie kluczy (<= 1024 bitów)   | ✔️         | ✔️    | ✔️            | ✔️           |
| Ładowanie kluczy (> 1024 bitów)    | ✔️         | ✔️    | ⚠️\*          | ❌            |
| FIPS 186-2                    | ✔️         | ✔️    | ✔️            | ✔️           |
| FIPS 186-3 (sygnatury SHA-2) | ✔️         | ✔️    | ❌            | ❌            |

\*macOS ładuje klucze DSA o rozmiarze większym niż 1024 bitów, ale zachowanie tych kluczy jest niezdefiniowane. Nie zachowują się one zgodnie z standardem FIPS 186-3.

#### <a name="dsa-on-windows"></a>Agent DSA w systemie Windows

* Interfejs Windows CryptoAPI (CAPI) jest używany zawsze, gdy [`new DSACryptoServiceProvider()`](xref:System.Security.Cryptography.DSACryptoServiceProvider) jest używany.
* Użycie usługi Windows Cryptography API Next Generation (CNG) jest używane za każdym razem, gdy [`new DSACng()`](xref:System.Security.Cryptography.DSACng) jest używany.
* Obiekt zwrócony przez <xref:System.Security.Cryptography.DSA.Create%2A?displayProperty=nameWithType> jest wewnętrznie obsługiwany przez CNG systemu Windows. Korzystanie z systemu Windows CNG jest szczegółami implementacji i może ulec zmianie.
* <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A>Metoda rozszerzająca dla <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> zwraca <xref:System.Security.Cryptography.DSACng> wystąpienia. To użycie <xref:System.Security.Cryptography.DSACng> jest szczegółami implementacji i może ulec zmianie.
* <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A>Metoda rozszerzająca dla <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> preferowanego <xref:System.Security.Cryptography.DSACng> wystąpienia, ale jeśli <xref:System.Security.Cryptography.DSACng> nie można otworzyć klucza, <xref:System.Security.Cryptography.DSACryptoServiceProvider> zostanie podjęta próba.  Preferowany dostawca jest szczegółami implementacji i może ulec zmianie.

#### <a name="dsa-native-interop"></a>Natywna międzyoperacyjność DSA

Platforma .NET udostępnia typy umożliwiające współdziałanie programów z bibliotekami systemu operacyjnego, które są używane przez kod kryptografii platformy .NET. Typy, których to dotyczy, nie są tłumaczone między platformami i powinny być bezpośrednio używane tylko wtedy, gdy jest to konieczne.

| Typ                                                         | Windows | Linux         | macOS         |
|--------------------------------------------------------------|---------|---------------|---------------|
| <xref:System.Security.Cryptography.DSACryptoServiceProvider> | ✔️     | ⚠️<sup>jedno</sup> | ⚠️<sup>jedno</sup> |
| <xref:System.Security.Cryptography.DSACng>                   | ✔️     | ❌             | ❌            |
| <xref:System.Security.Cryptography.DSAOpenSsl>               | ❌      | ✔️            | ⚠️<sup>dwóch</sup> |

<sup>1</sup> w systemach MacOS i Linux <xref:System.Security.Cryptography.DSACryptoServiceProvider> można używać w celu zapewnienia zgodności z istniejącymi programami. W takim przypadku każda metoda wymagająca międzyoperacyjności systemu, taka jak otwieranie klucza nazwanego, zgłasza <xref:System.PlatformNotSupportedException> .

<sup>2</sup> w macOS, <xref:System.Security.Cryptography.DSAOpenSsl> działa, jeśli zainstalowano OpenSSL i odpowiednie DYLIB libcrypto można znaleźć za pośrednictwem ładowania biblioteki dynamicznej. Jeśli nie można znaleźć odpowiedniej biblioteki, zostaną zgłoszone wyjątki.

## <a name="x509-certificates"></a>Certyfikaty X. 509

Większość obsługi certyfikatów X. 509 w programie .NET pochodzi z bibliotek systemu operacyjnego. Aby załadować certyfikat do wystąpienia programu <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> lub <xref:System.Security.Cryptography.X509Certificates.X509Certificate> w programie .NET, certyfikat musi być załadowany przez podstawową bibliotekę systemu operacyjnego.

### <a name="read-a-pkcs12pfx"></a>Odczytaj plik PKCS12/PFX

| Scenariusz                                     | Windows | Linux | macOS |
|----------------------------------------------|---------|-------|-------|
| Pusty                                        | ✔️     | ✔️    | ✔️   |
| Jeden certyfikat, brak klucza prywatnego              | ✔️     | ✔️    | ✔️   |
| Jeden certyfikat z kluczem prywatnym            | ✔️     | ✔️    | ✔️   |
| Wiele certyfikatów, brak kluczy prywatnych       | ✔️     | ✔️    | ✔️   |
| Wiele certyfikatów, jeden klucz prywatny       | ✔️     | ✔️    | ✔️   |
| Wiele certyfikatów, wiele kluczy prywatnych | ✔️     | ⚠️\*  | ✔️   |

\*Dostępne w wersji zapoznawczej programu .NET 5.

### <a name="write-a-pkcs12pfx"></a>Napisz plik PKCS12/PFX

| Scenariusz                                     | Windows | Linux | macOS |
|----------------------------------------------|---------|-------|-------|
| Pusty                                        | ✔️     | ✔️    | ⚠️\* |
| Jeden certyfikat, brak klucza prywatnego              | ✔️     | ✔️    | ⚠️\* |
| Jeden certyfikat z kluczem prywatnym            | ✔️     | ✔️    | ✔️   |
| Wiele certyfikatów, brak kluczy prywatnych       | ✔️     | ✔️    | ⚠️\* |
| Wiele certyfikatów, jeden klucz prywatny       | ✔️     | ✔️    | ✔️   |
| Wiele certyfikatów, wiele kluczy prywatnych | ✔️     | ⚠️\*  | ✔️   |
| Ładowanie tymczasowe                            | ✔️     | ✔️    | ⚠️\* |

\*Dostępne w wersji zapoznawczej programu .NET 5.

macOS nie może załadować kluczy prywatnych certyfikatu bez obiektu pęku kluczy, co wymaga zapisu na dysku. Łańcuchy kluczy są tworzone automatycznie na potrzeby ładowania pliku PFX i są usuwane, gdy nie są już używane. Ponieważ <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> opcja oznacza, że klucz prywatny nie powinien być zapisywana na dysku, potwierdzenie flagi na macOS powoduje <xref:System.PlatformNotSupportedException> .

### <a name="write-a-pkcs7-certificate-collection"></a>Napisz kolekcję certyfikatów PKCS7

Systemy Windows i Linux emitują kodowane w formacie DER obiekty blob. macOS emituje obiekty blob w formacie nieokreślonym przez CER.

### <a name="x509store"></a>X509Store

W systemie Windows <xref:System.Security.Cryptography.X509Certificates.X509Store> Klasa jest reprezentacją interfejsów API magazynu certyfikatów systemu Windows. Te interfejsy API działają tak samo w oprogramowaniu .NET Core i .NET 5, jak w .NET Framework.

W systemie Linux <xref:System.Security.Cryptography.X509Certificates.X509Store> Klasa jest projekcją decyzji o zaufaniu systemu (tylko do odczytu), decyzji zaufania użytkownika (do odczytu i zapisu) oraz do magazynu kluczy użytkownika (do odczytu i zapisu).

W macOS, <xref:System.Security.Cryptography.X509Certificates.X509Store> Klasa jest projekcją decyzji o zaufaniu systemu (tylko do odczytu), decyzji zaufania użytkownika (tylko do odczytu) i magazynu kluczy użytkownika (do odczytu i zapisu).

W poniższych tabelach przedstawiono, które scenariusze są obsługiwane na każdej platformie. W przypadku nieobsługiwanych scenariuszy ( ❌ w tabelach) <xref:System.Security.Cryptography.CryptographicException> jest zgłaszany.

#### <a name="the-my-store"></a>Mój sklep

| Scenariusz                                         | Windows | Linux | macOS |
|--------------------------------------------------|---------|-------|-------|
| Otwórz CurrentUser\My (tylko do odczytu)                   | ✔️     | ✔️    | ✔️   |
| Otwórz CurrentUser\My (ReadWrite)                  | ✔️     | ✔️    | ✔️   |
| Otwórz CurrentUser\My (ExistingOnly)               | ✔️     | ⚠️    | ✔️   |
| Otwórz LocalMachine\My                             | ✔️     | ❌    | ✔️   |

W systemie Linux magazyny są tworzone przy pierwszym zapisie, a żadne magazyny użytkownika domyślnie nie istnieją, więc otwarcie `CurrentUser\My` z programu `ExistingOnly` może zakończyć się niepowodzeniem.

W witrynie macOS `CurrentUser\My` Magazyn jest domyślnym łańcuchem kluczy użytkownika, który jest `login.keychain` domyślnie. `LocalMachine\My`Sklep to `System.keychain` .

#### <a name="the-root-store"></a>Magazyn główny

| Scenariusz                              | Windows | Linux | macOS           |
|---------------------------------------|---------|-------|-----------------|
| Otwórz CurrentUser\Root (tylko do odczytu)      | ✔️     | ✔️    | ✔️             |
| Otwórz CurrentUser\Root (ReadWrite)     | ✔️     | ✔️    | ❌              |
| Otwórz CurrentUser\Root (ExistingOnly)  | ✔️     | ⚠️    | ✔️ (jeśli tylko do odczytu) |
| Otwórz LocalMachine\Root (tylko do odczytu)     | ✔️     | ✔️    | ✔️             |
| Otwórz LocalMachine\Root (ReadWrite)    | ✔️     | ❌    | ❌              |
| Otwórz LocalMachine\Root (ExistingOnly) | ✔️     | ⚠️    | ✔️ (jeśli tylko do odczytu) |

W systemie Linux `LocalMachine\Root` Magazyn jest interpretacją pakietu urzędu certyfikacji w domyślnej ścieżce dla OpenSSL.

W systemie macOS `CurrentUser\Root` Magazyn jest interpretacją `SecTrustSettings` wyników dla domeny zaufania użytkownika. `LocalMachine\Root`Magazyn to interpretacja `SecTrustSettings` wyników dla administratorów i domen zaufania systemu.

#### <a name="the-intermediate-store"></a>Magazyn pośredni

| Scenariusz                                      | Windows | Linux | macOS           |
|-----------------------------------------------|---------|-------|-----------------|
| Otwórz CurrentUser\Intermediate (tylko do odczytu)      | ✔️     | ✔️    | ✔️             |
| Otwórz CurrentUser\Intermediate (ReadWrite)     | ✔️     | ✔️    | ❌              |
| Otwórz CurrentUser\Intermediate (ExistingOnly)  | ✔️     | ⚠️    | ✔️ (jeśli tylko do odczytu) |
| Otwórz LocalMachine\Intermediate (tylko do odczytu)     | ✔️     | ✔️    | ✔️             |
| Otwórz LocalMachine\Intermediate (ReadWrite)    | ✔️     | ❌    | ❌              |
| Otwórz LocalMachine\Intermediate (ExistingOnly) | ✔️     | ⚠️    | ✔️ (jeśli tylko do odczytu) |

W systemie Linux `CurrentUser\Intermediate` Magazyn jest używany jako pamięć podręczna podczas pobierania pośrednich urzędów certyfikacji przy użyciu rekordów dostępu do informacji o urzędach w przypadku pomyślne kompilacje X509Chain. `LocalMachine\Intermediate`Magazyn jest interpretacją pakietu urzędu certyfikacji w domyślnej ścieżce dla OpenSSL.

#### <a name="the-disallowed-store"></a>Niedozwolony magazyn

| Scenariusz                                    | Windows | Linux | macOS           |
|---------------------------------------------|---------|-------|-----------------|
| Otwórz CurrentUser\Disallowed (tylko do odczytu)      | ✔️     | ⚠️    | ✔️             |
| Otwórz CurrentUser\Disallowed (ReadWrite)     | ✔️     | ⚠️    | ❌              |
| Otwórz CurrentUser\Disallowed (ExistingOnly)  | ✔️     | ⚠️    | ✔️ (jeśli tylko do odczytu) |
| Otwórz LocalMachine\Disallowed (tylko do odczytu)     | ✔️     | ❌    | ✔️             |
| Otwórz LocalMachine\Disallowed (ReadWrite)    | ✔️     | ❌    | ❌              |
| Otwórz LocalMachine\Disallowed (ExistingOnly) | ✔️     | ❌    | ✔️ (jeśli tylko do odczytu) |

W systemie Linux `Disallowed` Magazyn nie jest używany w budowaniu łańcucha i próba dodania do niego zawartości jest wynikiem <xref:System.Security.Cryptography.CryptographicException> . <xref:System.Security.Cryptography.CryptographicException>Jest zgłaszany podczas otwierania `Disallowed` sklepu, jeśli już uzyskał zawartość.

W macOS magazyny CurrentUser\Disallowed i LocalMachine\Disallowed to interpretacje odpowiednich SecTrustSettings wyników dla certyfikatów, których zaufanie jest ustawione na `Always Deny` .

#### <a name="nonexistent-store"></a>Nieistniejący magazyn

| Scenariusz                                         | Windows | Linux | macOS |
|--------------------------------------------------|---------|-------|-------|
| Otwórz nieistniejący magazyn (ExistingOnly)           | ❌     | ❌     | ❌    |
| Otwórz nieistniejący magazyn CurrentUser (ReadWrite)  | ✔️     | ✔️     | ⚠️   |
| Otwórz nieistniejący magazyn LocalMachine (ReadWrite) | ✔️     | ❌     | ❌    |

W systemie macOS Tworzenie niestandardowego magazynu za pomocą interfejsu API X509Store jest obsługiwane tylko dla `CurrentUser` lokalizacji. Spowoduje to utworzenie nowego łańcucha kluczy bez hasła w katalogu pęku kluczy użytkownika (*~/Library/Keychains*). Aby utworzyć łańcuch kluczy z hasłem, można użyć elementu P/Invoke `SecKeychainCreate` . Podobnie, można `SecKeychainOpen` użyć do otwierania łańcuchów kluczy w różnych lokalizacjach. Wyniki `IntPtr` mogą być przesyłane do programu [`new X509Store(IntPtr)`](xref:System.Security.Cryptography.X509Certificates.X509Store.%23ctor(System.IntPtr)) w celu uzyskania magazynu z możliwością odczytu i zapisu, z zastrzeżeniem uprawnień bieżącego użytkownika.

### <a name="x509chain"></a>X509Chain

macOS nie obsługuje użycia list CRL w trybie offline, więc `X509RevocationMode.Offline` jest traktowany jako `X509RevocationMode.Online` .

macOS nie obsługuje limitu czasu zainicjowane przez użytkownika w odniesieniu do listy CRL (lista odwołania certyfikatów)/OCSP (protokół stanu certyfikatu online)/AIA (dostęp do informacji o urzędach), więc `X509ChainPolicy.UrlRetrievalTimeout` jest ignorowany.

## <a name="additional-resources"></a>Dodatkowe zasoby

* [Model kryptografii .NET](cryptography-model.md)
* [Usługi kryptograficzne platformy .NET](cryptographic-services.md)
