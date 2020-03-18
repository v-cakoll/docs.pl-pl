---
title: Luka w zabezpieczeniach związana z odszyfrowywaniem CBC
description: Dowiedz się, jak wykrywać i ograniczać luki w czasie za pomocą symetrycznego odszyfrowywania w trybie szyfrowania i łańcucha blokowego (CBC) przy użyciu dopełnienia.
ms.date: 06/12/2018
author: blowdart
ms.openlocfilehash: 47520ea4c9c7d0ef4d79378c93c6ce1f2ba7dd6d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186099"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a>Luki w zabezpieczeniach chronometrażu z odszyfrowywaniem symetrycznym w trybie CBC przy użyciu uzupełnienia

Microsoft uważa, że nie jest już bezpieczne odszyfrowywanie danych zaszyfrowanych za pomocą trybu szyfrowania szyfrowania szyfrującego(CBC) szyfrowania symetrycznego, gdy zastosowano weryfikowalne dopełnienie bez uprzedniego zapewnienia integralności szyfru, z wyjątkiem bardzo specyficznych Okolicznościach. Wyrok ten opiera się na obecnie znanych badaniach kryptograficznych.

## <a name="introduction"></a>Wprowadzenie

Atak oracle dopełnienie jest rodzajem ataku na zaszyfrowane dane, który umożliwia osobie atakującej odszyfrowywanie zawartości danych, bez znajomości klucza.

Oracle odnosi się do "powiedz", który daje osobie atakującej informacje o tym, czy wykonywana akcja jest poprawna, czy nie. Wyobraź sobie, że grasz z dzieckiem na planszy lub w grę karcianą. Kiedy ich twarz zapala się z wielkim uśmiechem, ponieważ myślą, że mają zamiar zrobić dobry ruch, to wyrocznia. Ty, jako przeciwnik, możesz użyć tej wyroczni, aby odpowiednio zaplanować swój następny ruch.

Dopełnienie to określony termin kryptograficzny. Niektóre szyfry, które są algorytmami używanymi do szyfrowania danych, działają na blokach danych, gdzie każdy blok ma stały rozmiar. Jeśli dane, które chcesz zaszyfrować, nie są odpowiednim rozmiarem do wypełnienia bloków, dane są wypełniane, dopóki tego nie zrobisz. Wiele form dopełnienia wymagają, aby dopełnienie było zawsze obecne, nawet jeśli oryginalne dane wejściowe były o odpowiednim rozmiarze. Dzięki temu dopełnienie zawsze być bezpiecznie usunięte po odszyfrowywaniu.

Łącząc te dwie rzeczy razem, implementacja oprogramowania z oracle dopełnienie ujawnia, czy odszyfrowane dane mają prawidłową dopełnienie. Oracle może być coś tak proste, jak zwracanie wartości, która mówi "Nieprawidłowe dopełnienie" lub coś bardziej skomplikowanego, jak biorąc wymiernie inny czas do przetworzenia prawidłowego bloku, w przeciwieństwie do nieprawidłowego bloku.

Szyfry oparte na blokach mają inną właściwość, o nazwie tryb, która określa relację danych w pierwszym bloku do danych w drugim bloku i tak dalej. Jednym z najczęściej używanych trybów jest CBC. CBC wprowadza początkowy blok losowy, znany jako Wektor inicjowania (IV) i łączy poprzedni blok z wynikiem szyfrowania statycznego, aby uczynić go tak, że szyfrowanie tej samej wiadomości za pomocą tego samego klucza nie zawsze daje te same szyfrowane dane wyjściowe.

Osoba atakująca może użyć oracle dopełnienia, w połączeniu z jak dane CBC jest zorganizowany, aby wysłać nieco zmienione wiadomości do kodu, który udostępnia oracle i zachować wysyłanie danych, dopóki oracle mówi im, że dane są poprawne. Z tej odpowiedzi osoba atakująca może odszyfrować bajt wiadomości według bajtu.

Nowoczesne sieci komputerowe są tak wysokiej jakości, że osoba atakująca może wykryć bardzo małe (mniej niż 0,1 ms) różnice w czasie wykonywania w systemach zdalnych.Aplikacje, które są przy założeniu, że pomyślne odszyfrowywanie może się zdarzyć tylko wtedy, gdy dane nie zostały naruszone, mogą być narażone na ataki z narzędzi, które są przeznaczone do obserwowania różnic w pomyślnym i nieudanym odszyfrowywaniu. Chociaż ta różnica czasu może być bardziej istotne w niektórych językach lub bibliotekach niż inne, teraz uważa się, że jest to praktyczne zagrożenie dla wszystkich języków i bibliotek, gdy odpowiedź aplikacji na niepowodzenie jest brana pod uwagę.

Ten atak opiera się na możliwości zmiany zaszyfrowanych danych i przetestowania wyniku za pomocą oracle. Jedynym sposobem, aby w pełni złagodzić atak jest wykrycie zmian w zaszyfrowanych danych i odmówić wykonania jakichkolwiek działań na nim. Standardowym sposobem, aby to zrobić jest utworzenie podpisu dla danych i sprawdzić poprawność tego podpisu przed wykonaniem jakichkolwiek operacji. Podpis musi być weryfikowalny, nie może zostać utworzony przez osobę atakującą, w przeciwnym razie zmieniłby zaszyfrowane dane, a następnie obliczyć nowy podpis na podstawie zmienionych danych. Jeden typowy typ odpowiedniego podpisu jest znany jako kod uwierzytelniania komunikatów klucza mieszania (HMAC). HMAC różni się od sumy kontrolnej tym, że zajmuje tajny klucz, znany tylko osobie produkującej HMAC i osobie zatwierdzającej go. Bez posiadania klucza, nie można produkować poprawne HMAC. Po otrzymaniu danych należy wziąć zaszyfrowane dane, niezależnie obliczyć HMAC przy użyciu klucza tajnego, który ty i udział nadawcy, a następnie porównać HMAC, który wysłali z tym, który został obliczony. To porównanie musi być stałym czasem, w przeciwnym razie dodano inną wykrywalną wyrocznię, umożliwiając ą inny typ ataku.

Podsumowując, aby bezpiecznie używać wyściełanych szyfrów bloków CBC, należy połączyć je z hmac (lub innym sprawdzaniem integralności danych), które można sprawdzić przy użyciu stałego porównania czasu przed próbą odszyfrowania danych. Ponieważ wszystkie zmienione wiadomości zajmują tyle samo czasu, aby wygenerować odpowiedź, atak jest zapobiegany.

## <a name="who-is-vulnerable"></a>Kto jest podatny na zagrożenia

Ta luka dotyczy zarówno aplikacji zarządzanych, jak i natywnych, które wykonują własne szyfrowanie i odszyfrowywanie. Obejmuje to na przykład:

- Aplikacja, która szyfruje plik cookie do późniejszego odszyfrowywania na serwerze.
- Aplikacja bazy danych, która zapewnia użytkownikom możliwość wstawiania danych do tabeli, której kolumny są później odszyfrowywane.
- Aplikacja do przesyłania danych, która opiera się na szyfrowaniu przy użyciu klucza udostępnionego w celu ochrony danych podczas przesyłania.
- Aplikacja, która szyfruje i odszyfrowuje wiadomości "wewnątrz" tunelu TLS.

Należy pamiętać, że przy użyciu samego protokołu TLS może nie chronić cię w tych scenariuszach.

Aplikacja podatna na ataki:

- Odszyfrowuje dane przy użyciu trybu szyfrowania CBC z weryfikowalnym trybem dopełnienia, takim jak PKCS#7 lub ANSI X.923.
- Wykonuje odszyfrowywanie bez przeprowadzania sprawdzania integralności danych (za pomocą maca lub asymetrycznego podpisu cyfrowego).

Dotyczy to również aplikacji zbudowanych na abstrakcjach nad tymi pierwotnymi, takich jak struktura Koperta wiadomości kryptograficznych (PKCS#7/CMS).

## <a name="related-areas-of-concern"></a>Powiązane obszary budzące obawy

Badania doprowadziły Microsoft być dalej zaniepokojony wiadomości CBC, które są wyściełane iso 10126 równoważne dopełnienia, gdy wiadomość ma dobrze znaną lub przewidywalną strukturę stopki. Na przykład zawartość przygotowana zgodnie z regułami W3C XML Encryption Syntax and Processing Recommendation (xmlenc, EncryptedXml). Podczas gdy wskazówki W3C do podpisania wiadomości następnie szyfrowania uznano za odpowiednie w tym czasie, Microsoft zaleca teraz zawsze robi szyfrowania, a następnie znak.

Deweloperzy aplikacji zawsze powinni mieć na uwadze sprawdzanie możliwości zastosowania asymetrycznego klucza podpisu, ponieważ nie ma nieodłącznej relacji zaufania między kluczem asymetrycznym a dowolną wiadomością.

## <a name="details"></a>Szczegóły

Historycznie istniała zgoda co do tego, że ważne jest, aby zarówno szyfrować, jak i uwierzytelniać ważne dane przy użyciu środków, takich jak podpisy HMAC lub RSA. Jednak było mniej jasne wskazówki dotyczące sposobu sekwencjonowania operacji szyfrowania i uwierzytelniania. Ze względu na lukę w zabezpieczeniach wyszczególnioną w tym artykule wskazówki firmy Microsoft są teraz zawsze używane do paradygmatu "szyfrowanie, a następnie znak". Oznacza to, że najpierw zaszyfruj dane przy użyciu klucza symetrycznego, a następnie obłamuje podpis MAC lub asymetryczny za pomocą szyfru (zaszyfrowanych danych). Podczas odszyfrowywania danych wykonaj odwrotnie. Najpierw potwierdź MAC lub podpis szyfru, a następnie odszyfruj go.

Wiadomo, że od ponad 10 lat istnieje klasa luk w zabezpieczeniach znana jako "ataki wyroczni" dopełnianie. Luki te umożliwiają osobie atakującej odszyfrowanie danych zaszyfrowanych za pomocą symetrycznych algorytmów blokowych, takich jak AES i 3DES, przy użyciu nie więcej niż 4096 prób na blok danych. Luki te wykorzystują fakt, że szyfry blokowe są najczęściej używane z weryfikowalnymi danymi dopełnienia na końcu. Stwierdzono, że jeśli osoba atakująca może manipulować szyfrem i dowiedzieć się, czy naruszenie spowodowało błąd w formacie dopełnienia na końcu, osoba atakująca może odszyfrować dane.

Początkowo praktyczne ataki były oparte na usługach, które zwracałyby różne kody błędów w zależności od tego, czy dopełnienie było prawidłowe, takie jak ASP.NET luka [MS10-070](/security-updates/SecurityBulletins/2010/ms10-070). Jednak Microsoft uważa teraz, że jest to praktyczne do przeprowadzenia podobnych ataków przy użyciu tylko różnice w czasie między przetwarzania prawidłowe i nieprawidłowe dopełnienia.

Pod warunkiem, że schemat szyfrowania wykorzystuje podpis i że weryfikacja podpisu jest wykonywana ze stałym czasem wykonywania dla danej długości danych (niezależnie od zawartości), integralność danych może być zweryfikowana bez emitowania jakichkolwiek informacji osobie atakującej za pośrednictwem [kanału bocznego](https://en.wikipedia.org/wiki/Side-channel_attack). Ponieważ sprawdzanie integralności odrzuca wszelkie zmodyfikowane wiadomości, zagrożenie oracle dopełnianie jest złagodzone.

## <a name="guidance"></a>Wskazówki

Przede wszystkim firma Microsoft zaleca, aby wszelkie dane, które mają poufność, były przesyłane za pośrednictwem protokołu TLS (Transport Layer Security), następcy aplikacji Secure Sockets Layer (SSL).

Następnie przeanalizuj aplikację, aby:

- Dokładnie dowiedz się, jakie szyfrowanie wykonujesz i jakie szyfrowanie jest dostarczane przez platformy i interfejsy API, których używasz.
- Upewnij się, że każde użycie w każdej warstwie [algorytmu szyfrowania bloku](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers)symetrycznego , takiego jak AES i 3DES, w trybie CBC obejmuje użycie sprawdzania integralności danych z kluczem tajnym (podpis asymetryczny, HMAC lub w celu zmiany trybu szyfrowania na tryb [uwierzytelniania szyfrowania](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE), takiego jak GCM lub CCM).

Na podstawie bieżących badań, ogólnie uważa się, że gdy kroki uwierzytelniania i szyfrowania są wykonywane niezależnie dla trybów szyfrowania innych niż AE, uwierzytelnianie szyfrowania (szyfrowanie,a następnie znak) jest najlepszym rozwiązaniem ogólnym. Jednak nie ma jednej uniwersalnej poprawnej odpowiedzi na kryptografię, a to uogólnienie nie jest tak dobre, jak skierowane porady profesjonalnego kryptografa.

Aplikacje, które nie mogą zmienić formatu obsługi wiadomości, ale wykonują nieuwierzytelnione odszyfrowywanie CBC, są zachęcane do próby włączenia czynników ograniczających zagrożenie, takich jak:

- Odszyfruj bez zezwolenia deszyfratorowi na weryfikację lub usunięcie dopełnienia:
  - Wszelkie dopełnienie, które zostały zastosowane nadal musi zostać usunięty lub zignorowany, przenosisz obciążenie do aplikacji.
  - Zaletą jest to, że weryfikacja i usuwanie dopełnienia mogą być włączone do innej logiki weryfikacji danych aplikacji. Jeśli weryfikacja dopełnienia i weryfikacja danych mogą być wykonywane w stałym czasie, zagrożenie jest zmniejszone.
  - Ponieważ interpretacja dopełnienie zmienia długość wiadomości postrzegane, nadal mogą istnieć informacje o czasie emitowane z tego podejścia.
- Zmień tryb dopełnienia odszyfrowywania na ISO10126:
  - Dopełnienie deszyfrujące ISO10126 jest zgodne zarówno z dopełnieniem szyfrowania PKCS7, jak i dopełnieniem szyfrowania ANSIX923.
  - Zmiana trybu zmniejsza dopełnienie oracle wiedzy do 1 bajt zamiast całego bloku. Jeśli jednak zawartość ma dobrze znaną stopkę, taką jak zamykający element XML, powiązane ataki mogą nadal atakować pozostałą część wiadomości.
  - Nie uniemożliwia to również odzyskiwania zwykłego tekstu w sytuacjach, gdy osoba atakująca może zmuszać ten sam zwykły tekst do wielokrotnego szyfrowania za pomocą innego przesunięcia wiadomości.
- Gate oceny wywołania odszyfrowywania, aby tłumić sygnał rozrządu:
  - Obliczenia czasu wstrzymania musi mieć minimum powyżej maksymalnej ilości czasu operacji odszyfrowywania zajmie dla dowolnego segmentu danych, który zawiera dopełnienie.
  - Obliczenia czasu powinny być wykonywane zgodnie ze wskazówkami w [Uzyskiwanie sygnatury czasowe o wysokiej rozdzielczości,](/windows/desktop/sysinfo/acquiring-high-resolution-time-stamps)a nie za pomocą <xref:System.Environment.TickCount?displayProperty=nameWithType> (z zastrzeżeniem roll-over/overflow) lub odejmowanie dwóch sygnatury czasowe systemu (z zastrzeżeniem błędów regulacji NTP).
  - Obliczenia czasu musi zawierać operacji odszyfrowywania, w tym wszystkie potencjalne wyjątki w zarządzanych lub aplikacji C++, a nie tylko wyściełane na końcu.
  - Jeśli sukces lub niepowodzenie zostało jeszcze ustalone, brama chronometrażu musi zwrócić błąd po wygaśnięciu.
- Usługi, które wykonują nieuwierzytelnione odszyfrowywanie powinny mieć monitorowanie w celu wykrycia, że zalew "nieprawidłowych" komunikatów przeszła.
  - Należy pamiętać, że sygnał ten niesie zarówno fałszywe alarmy (legalnie uszkodzone dane), jak i fałszywe negatywy (rozprzestrzenianie ataku na wystarczająco długi czas, aby uniknąć wykrycia).

## <a name="finding-vulnerable-code---native-applications"></a>Znajdowanie kodu podlegania usterce — aplikacje natywne

Dla programów zbudowanych na przeciwko windows kryptografii: Nowej Generacji (CNG) biblioteki:

- Wywołanie odszyfrowywania jest [BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt), `BCRYPT_BLOCK_PADDING` określając flagę.
- Dojście klucza zostało zainicjowane przez [BCRYPT_CHAINING_MODE](/windows/desktop/SecCNG/cng-property-identifiers#BCRYPT_CHAINING_MODE) wywołanie `BCRYPT_CHAIN_MODE_CBC` [BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty) z BCRYPT_CHAINING_MODE ustawionym na .
  - Ponieważ `BCRYPT_CHAIN_MODE_CBC` jest to wartość domyślna, kod, `BCRYPT_CHAINING_MODE`którego dotyczy problem, może nie przypisać żadnej wartości dla .

W przypadku programów utworzonych w ramach starszego kryptograficznego interfejsu API systemu Windows:

- Wywołanie odszyfrowywania jest [CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) z `Final=TRUE`.
- Dojście klucza zostało zainicjowane przez wywołanie [CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam) z [KP_MODE](/windows/desktop/api/wincrypt/nf-wincrypt-cryptgetkeyparam) ustawionym na `CRYPT_MODE_CBC`.
  - Ponieważ `CRYPT_MODE_CBC` jest to wartość domyślna, kod, `KP_MODE`którego dotyczy problem, może nie przypisać żadnej wartości dla .

## <a name="finding-vulnerable-code---managed-applications"></a>Znajdowanie kodu podlegania usterce — aplikacje zarządzane

- Wywołanie odszyfrowywania jest <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> do lub <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>metody na .
  - Obejmuje to następujące typy pochodne w ramach .NET, ale może również obejmować typy innych firm:
    - <xref:System.Security.Cryptography.Aes>
    - <xref:System.Security.Cryptography.AesCng>
    - <xref:System.Security.Cryptography.AesCryptoServiceProvider>
    - <xref:System.Security.Cryptography.AesManaged>
    - <xref:System.Security.Cryptography.DES>
    - <xref:System.Security.Cryptography.DESCryptoServiceProvider>
    - <xref:System.Security.Cryptography.RC2>
    - <xref:System.Security.Cryptography.RC2CryptoServiceProvider>
    - <xref:System.Security.Cryptography.Rijndael>
    - <xref:System.Security.Cryptography.RijndaelManaged>
    - <xref:System.Security.Cryptography.TripleDES>
    - <xref:System.Security.Cryptography.TripleDESCng>
    - <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>
- Właściwość <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> została ustawiona <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>na <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>, lub .
  - Ponieważ <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> jest to wartość domyślna, kod, którego dotyczy problem, może nigdy nie przypisał <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> właściwości.
- Obiekt <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> został ustawiony na<xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType>
  - Ponieważ <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> jest to wartość domyślna, kod, którego dotyczy problem, może nigdy nie przypisał <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> właściwości.

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a>Znajdowanie zagrożonego kodu — składnia wiadomości kryptograficznych

Nieuwierzytelniony komunikat CMS EnvelopedData, którego zaszyfrowana zawartość korzysta z trybu CBC AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) lub RC2 (1.2.840.113549.3.2) jest wrażliwych, a także wiadomości przy użyciu innych algorytmów szyfrowania blokowego w trybie CBC.

Szyfry strumienia nie są podatne na tę szczególną lukę w zabezpieczeniach, firma Microsoft zaleca zawsze uwierzytelnianie danych za pomocą sprawdzania wartości ContentEncryptionAlgorithm.

W przypadku aplikacji zarządzanych obiekt blob CMS EnvelopedData można <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>wykryć jako dowolną wartość, która jest przekazywana do .

W przypadku aplikacji natywnych obiekt blob CMS EnvelopedData można wykryć jako dowolną [CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam) wartość `CMSG_ENVELOPED` dostarczoną do dojścia CMS za pośrednictwem [CryptMsgUpdate,](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) którego wynikowy CMSG_TYPE_PARAM jest i/lub dojście CMS jest później wysyłane instrukcję `CMSG_CTRL_DECRYPT` za pośrednictwem [CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol).

## <a name="vulnerable-code-example---managed"></a>Przykład kodu podatny na zagrożenia — zarządzany

Ta metoda odczytuje plik cookie i odszyfrowuje go, a kontrola integralności danych nie jest widoczna. W związku z tym zawartość pliku cookie odczytywanego przez tę metodę może zostać zaatakowana przez użytkownika, który go otrzymał, lub przez osobę atakującą, która uzyskała zaszyfrowaną wartość pliku cookie.

```csharp
private byte[] DecryptCookie(string cookieName)
{
    HttpCookie cookie = Request.Cookies[cookieName];

    if (cookie == null)
    {
        return null;
    }

    using (ICryptoTransform decryptor = _aes.CreateDecryptor())
    using (MemoryStream memoryStream = new MemoryStream())
    using (CryptoStream cryptoStream =
        new CryptoStream(memoryStream, decryptor, CryptoStreamMode.Write))
    {
        byte[] readCookie = Convert.FromBase64String(cookie.Value);
        cryptoStream.Write(readCookie, 0, readCookie.Length);
        cryptoStream.FlushFinalBlock();
        return memoryStream.ToArray();
    }
}
```

## <a name="example-code-following-recommended-practices---managed"></a>Przykładowy kod po zalecanych praktykach — zarządzany

Poniższy przykładowy kod używa niestandardowego formatu wiadomości

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

gdzie `cipher_algorithm_id` identyfikatory i `hmac_algorithm_id` algorytmsą lokalnymi (niestandardowymi) reprezentacjami tych algorytmów. Identyfikatory te mogą mieć sens w innych częściach istniejącego protokołu obsługi wiadomości, a nie jako gołe połączony bytestream.

W tym przykładzie użyto również pojedynczego klucza głównego do uzyskania zarówno klucza szyfrowania, jak i klucza HMAC. Jest to zarówno jako wygoda dla przełączania aplikacji z singly-keyed do aplikacji z dwoma kluczami, jak i zachęcanie do zachowania dwóch kluczy jako różnych wartości. Ponadto gwarantuje, że klucz HMAC i klucz szyfrowania nie mogą wydostać się z synchronizacji.

W tym przykładzie nie <xref:System.IO.Stream> akceptuje szyfrowania lub odszyfrowywania. Bieżący format danych utrudnia szyfrowanie jednoprzebiegowe, `hmac_tag` ponieważ wartość poprzedza szyfrtekst. Jednak ten format został wybrany, ponieważ zachowuje wszystkie elementy o stałym rozmiarze na początku, aby uprościć analizator. W tym formacie danych, one-pass odszyfrowywania jest możliwe, choć realizator jest ostrzegany, aby wywołać GetHashAndReset i sprawdzić wynik przed wywołaniem TransformFinalBlock. Jeśli szyfrowanie przesyłania strumieniowego jest ważne, może być wymagany inny tryb AE.

```csharp
// ==++==
//
//   Copyright (c) Microsoft Corporation.  All rights reserved.
//
//   Shared under the terms of the Microsoft Public License,
//   https://opensource.org/licenses/MS-PL
//
// ==--==

using System;
using System.Diagnostics;
using System.IO;
using System.Runtime.CompilerServices;
using System.Security.Cryptography;

namespace Microsoft.Examples.Cryptography
{
    public enum AeCipher : byte
    {
        Unknown,
        Aes256CbcPkcs7,
    }

    public enum AeMac : byte
    {
        Unknown,
        HMACSHA256,
        HMACSHA384,
    }

    /// <summary>
    /// Provides extension methods to make HashAlgorithm look like .NET Core's
    /// IncrementalHash
    /// </summary>
    internal static class IncrementalHashExtensions
    {
        public static void AppendData(this HashAlgorithm hash, byte[] data)
        {
            hash.TransformBlock(data, 0, data.Length, null, 0);
        }

        public static void AppendData(
            this HashAlgorithm hash,
            byte[] data,
            int offset,
            int length)
        {
            hash.TransformBlock(data, offset, length, null, 0);
        }

        public static byte[] GetHashAndReset(this HashAlgorithm hash)
        {
            hash.TransformFinalBlock(Array.Empty<byte>(), 0, 0);
            return hash.Hash;
        }
    }

    public static partial class AuthenticatedEncryption
    {
        /// <summary>
        /// Use <paramref name="masterKey"/> to derive two keys (one cipher, one HMAC)
        /// to provide authenticated encryption for <paramref name="message"/>.
        /// </summary>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <param name="message">The message to encrypt</param>
        /// <returns>
        /// A concatenation of
        /// [cipher algorithm+chainmode+padding][mac algorithm][authtag][IV][ciphertext],
        /// suitable to be passed to <see cref="Decrypt"/>.
        /// </returns>
        /// <remarks>
        /// <paramref name="masterKey"/> should be a 128-bit (or bigger) value generated
        /// by a secure random number generator, such as the one returned from
        /// <see cref="RandomNumberGenerator.Create()"/>.
        /// This implementation chooses to block deficient inputs by length, but does not
        /// make any attempt at discerning the randomness of the key.
        ///
        /// If the master key is being input by a prompt (like a password/passphrase)
        /// then it should be properly turned into keying material via a Key Derivation
        /// Function like PBKDF2, represented by Rfc2898DeriveBytes. A 'password' should
        /// never be simply turned to bytes via an Encoding class and used as a key.
        /// </remarks>
        public static byte[] Encrypt(byte[] masterKey, byte[] message)
        {
            if (masterKey == null)
                throw new ArgumentNullException(nameof(masterKey));
            if (masterKey.Length < 16)
                throw new ArgumentOutOfRangeException(
                    nameof(masterKey),
                    "Master Key must be at least 128 bits (16 bytes)");
            if (message == null)
                throw new ArgumentNullException(nameof(message));

            // First, choose an encryption scheme.
            AeCipher aeCipher = AeCipher.Aes256CbcPkcs7;

            // Second, choose an authentication (message integrity) scheme.
            //
            // In this example we use the master key length to change from HMACSHA256 to
            // HMACSHA384, but that is completely arbitrary. This mostly represents a
            // "cryptographic needs change over time" scenario.
            AeMac aeMac = masterKey.Length < 48 ? AeMac.HMACSHA256 : AeMac.HMACSHA384;

            // It's good to be able to identify what choices were made when a message was
            // encrypted, so that the message can later be decrypted. This allows for
            // future versions to add support for new encryption schemes, but still be
            // able to read old data. A practice known as "cryptographic agility".
            //
            // This is similar in practice to PKCS#7 messaging, but this uses a
            // private-scoped byte rather than a public-scoped Object IDentifier (OID).
            // Please note that the scheme in this example adheres to no particular
            // standard, and is unlikely to survive to a more complete implementation in
            // the .NET Framework.
            //
            // You may be well-served by prepending a version number byte to this
            // message, but may want to avoid the value 0x30 (the leading byte value for
            // DER-encoded structures such as X.509 certificates and PKCS#7 messages).
            byte[] algorithmChoices = { (byte)aeCipher, (byte)aeMac };
            byte[] iv;
            byte[] cipherText;
            byte[] tag;

            // Using our algorithm choices, open an HMAC (as an authentication tag
            // generator) and a SymmetricAlgorithm which use different keys each derived
            // from the same master key.
            //
            // A custom implementation may very well have distinctly managed secret keys
            // for the MAC and cipher, this example merely demonstrates the master to
            // derived key methodology to encourage key separation from the MAC and
            // cipher keys.
            using (HMAC tagGenerator = GetMac(aeMac, masterKey))
            {
                using (SymmetricAlgorithm cipher = GetCipher(aeCipher, masterKey))
                using (ICryptoTransform encryptor = cipher.CreateEncryptor())
                {
                    // Since no IV was provided, a random one has been generated
                    // during the call to CreateEncryptor.
                    //
                    // But note that it only does the auto-generation once. If the cipher
                    // object were used again, a call to GenerateIV would have been
                    // required.
                    iv = cipher.IV;

                    cipherText = Transform(encryptor, message, 0, message.Length);
                }

                // The IV and ciphertest both need to be included in the MAC to prevent
                // tampering.
                //
                // By including the algorithm identifiers, we have technically moved from
                // simple Authenticated Encryption (AE) to Authenticated Encryption with
                // Additional Data (AEAD). By including the algorithm identifiers in the
                // MAC, it becomes harder for an attacker to change them as an attempt to
                // perform a downgrade attack.
                //
                // If you've added a data format version field, it can also be included
                // in the MAC to further inhibit an attacker's options for confusing the
                // data processor into believing the tampered message is valid.
                tagGenerator.AppendData(algorithmChoices);
                tagGenerator.AppendData(iv);
                tagGenerator.AppendData(cipherText);
                tag = tagGenerator.GetHashAndReset();
            }

            // Build the final result as the concatenation of everything except the keys.
            int totalLength =
                algorithmChoices.Length +
                tag.Length +
                iv.Length +
                cipherText.Length;

            byte[] output = new byte[totalLength];
            int outputOffset = 0;

            Append(algorithmChoices, output, ref outputOffset);
            Append(tag, output, ref outputOffset);
            Append(iv, output, ref outputOffset);
            Append(cipherText, output, ref outputOffset);

            Debug.Assert(outputOffset == output.Length);
            return output;
        }

        /// <summary>
        /// Reads a message produced by <see cref="Encrypt"/> after verifying it hasn't
        /// been tampered with.
        /// </summary>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <param name="cipherText">
        /// The output of <see cref="Encrypt"/>: a concatenation of a cipher ID, mac ID,
        /// authTag, IV, and cipherText.
        /// </param>
        /// <returns>The decrypted content.</returns>
        /// <exception cref="ArgumentNullException">
        /// <paramref name="masterKey"/> is <c>null</c>.
        /// </exception>
        /// <exception cref="ArgumentNullException">
        /// <paramref name="cipherText"/> is <c>null</c>.
        /// </exception>
        /// <exception cref="CryptographicException">
        /// <paramref name="cipherText"/> identifies unknown algorithms, is not long
        /// enough, fails a data integrity check, or fails to decrypt.
        /// </exception>
        /// <remarks>
        /// <paramref name="masterKey"/> should be a 128-bit (or larger) value
        /// generated by a secure random number generator, such as the one returned from
        /// <see cref="RandomNumberGenerator.Create()"/>. This implementation chooses to
        /// block deficient inputs by length, but doesn't make any attempt at
        /// discerning the randomness of the key.
        ///
        /// If the master key is being input by a prompt (like a password/passphrase),
        /// then it should be properly turned into keying material via a Key Derivation
        /// Function like PBKDF2, represented by Rfc2898DeriveBytes. A 'password' should
        /// never be simply turned to bytes via an Encoding class and used as a key.
        /// </remarks>
        public static byte[] Decrypt(byte[] masterKey, byte[] cipherText)
        {
            // This example continues the .NET practice of throwing exceptions for
            // failures. If you consider message tampering to be normal (and thus
            // "not exceptional") behavior, you may like the signature
            // bool Decrypt(byte[] messageKey, byte[] cipherText, out byte[] message)
            // better.
            if (masterKey == null)
                throw new ArgumentNullException(nameof(masterKey));
            if (masterKey.Length < 16)
                throw new ArgumentOutOfRangeException(
                    nameof(masterKey),
                    "Master Key must be at least 128 bits (16 bytes)");
            if (cipherText == null)
                throw new ArgumentNullException(nameof(cipherText));

            // The format of this message is assumed to be public, so there's no harm in
            // saying ahead of time that the message makes no sense.
            if (cipherText.Length < 2)
            {
                throw new CryptographicException();
            }

            // Use the message algorithm headers to determine what cipher algorithm and
            // MAC algorithm are going to be used. Since the same Key Derivation
            // Functions (KDFs) are being used in Decrypt as Encrypt, the keys are also
            // the same.
            AeCipher aeCipher = (AeCipher)cipherText[0];
            AeMac aeMac = (AeMac)cipherText[1];

            using (SymmetricAlgorithm cipher = GetCipher(aeCipher, masterKey))
            using (HMAC tagGenerator = GetMac(aeMac, masterKey))
            {
                int blockSizeInBytes = cipher.BlockSize / 8;
                int tagSizeInBytes = tagGenerator.HashSize / 8;
                int headerSizeInBytes = 2;
                int tagOffset = headerSizeInBytes;
                int ivOffset = tagOffset + tagSizeInBytes;
                int cipherTextOffset = ivOffset + blockSizeInBytes;
                int cipherTextLength = cipherText.Length - cipherTextOffset;
                int minLen = cipherTextOffset + blockSizeInBytes;

                // Again, the minimum length is still assumed to be public knowledge,
                // nothing has leaked out yet. The minimum length couldn't just be calculated
                // without reading the header.
                if (cipherText.Length < minLen)
                {
                    throw new CryptographicException();
                }

                // It's very important that the MAC be calculated and verified before
                // proceeding to decrypt the ciphertext, as this prevents any sort of
                // information leaking out to an attacker.
                //
                // Don't include the tag in the calculation, though.

                // First, everything before the tag (the cipher and MAC algorithm ids)
                tagGenerator.AppendData(cipherText, 0, tagOffset);

                // Skip the data before the tag and the tag, then read everything that
                // remains.
                tagGenerator.AppendData(
                    cipherText,
                    tagOffset + tagSizeInBytes,
                    cipherText.Length - tagSizeInBytes - tagOffset);

                byte[] generatedTag = tagGenerator.GetHashAndReset();

                // The time it took to get to this point has so far been a function only
                // of the length of the data, or of non-encrypted values (e.g. it could
                // take longer to prepare the *key* for the HMACSHA384 MAC than the
                // HMACSHA256 MAC, but the algorithm choice wasn't a secret).
                //
                // If the verification of the authentication tag aborts as soon as a
                // difference is found in the byte arrays then your program may be
                // acting as a timing oracle which helps an attacker to brute-force the
                // right answer for the MAC. So, it's very important that every possible
                // "no" (2^256-1 of them for HMACSHA256) be evaluated in as close to the
                // same amount of time as possible. For this, we call CryptographicEquals
                if (!CryptographicEquals(
                    generatedTag,
                    0,
                    cipherText,
                    tagOffset,
                    tagSizeInBytes))
                {
                    // Assuming every tampered message (of the same length) took the same
                    // amount of time to process, we can now safely say
                    // "this data makes no sense" without giving anything away.
                    throw new CryptographicException();
                }

                // Restore the IV into the symmetricAlgorithm instance.
                byte[] iv = new byte[blockSizeInBytes];
                Buffer.BlockCopy(cipherText, ivOffset, iv, 0, iv.Length);
                cipher.IV = iv;

                using (ICryptoTransform decryptor = cipher.CreateDecryptor())
                {
                    return Transform(
                        decryptor,
                        cipherText,
                        cipherTextOffset,
                        cipherTextLength);
                }
            }
        }

        private static byte[] Transform(
            ICryptoTransform transform,
            byte[] input,
            int inputOffset,
            int inputLength)
        {
            // Many of the implementations of ICryptoTransform report true for
            // CanTransformMultipleBlocks, and when the entire message is available in
            // one shot this saves on the allocation of the CryptoStream and the
            // intermediate structures it needs to properly chunk the message into blocks
            // (since the underlying stream won't always return the number of bytes
            // needed).
            if (transform.CanTransformMultipleBlocks)
            {
                return transform.TransformFinalBlock(input, inputOffset, inputLength);
            }

            // If our transform couldn't do multiple blocks at once, let CryptoStream
            // handle the chunking.
            using (MemoryStream messageStream = new MemoryStream())
            using (CryptoStream cryptoStream =
                new CryptoStream(messageStream, transform, CryptoStreamMode.Write))
            {
                cryptoStream.Write(input, inputOffset, inputLength);
                cryptoStream.FlushFinalBlock();
                return messageStream.ToArray();
            }
        }

        /// <summary>
        /// Open a properly configured <see cref="SymmetricAlgorithm"/> conforming to the
        /// scheme identified by <paramref name="aeCipher"/>.
        /// </summary>
        /// <param name="aeCipher">The cipher mode to open.</param>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <returns>
        /// A SymmetricAlgorithm object with the right key, cipher mode, and padding
        /// mode; or <c>null</c> on unknown algorithms.
        /// </returns>
        private static SymmetricAlgorithm GetCipher(AeCipher aeCipher, byte[] masterKey)
        {
            SymmetricAlgorithm symmetricAlgorithm;

            switch (aeCipher)
            {
                case AeCipher.Aes256CbcPkcs7:
                    symmetricAlgorithm = Aes.Create();
                    // While 256-bit, CBC, and PKCS7 are all the default values for these
                    // properties, being explicit helps comprehension more than it hurts
                    // performance.
                    symmetricAlgorithm.KeySize = 256;
                    symmetricAlgorithm.Mode = CipherMode.CBC;
                    symmetricAlgorithm.Padding = PaddingMode.PKCS7;
                    break;
                default:
                    // An algorithm we don't understand
                    throw new CryptographicException();
            }

            // Instead of using the master key directly, derive a key for our chosen
            // HMAC algorithm based upon the master key.
            //
            // Since none of the symmetric encryption algorithms currently in .NET
            // support key sizes greater than 256-bit, we can use HMACSHA256 with
            // NIST SP 800-108 5.1 (Counter Mode KDF) to derive a value that is
            // no smaller than the key size, then Array.Resize to trim it down as
            // needed.

            using (HMAC hmac = new HMACSHA256(masterKey))
            {
                // i=1, Label=ASCII(cipher)
                byte[] cipherKey = hmac.ComputeHash(
                    new byte[] { 1, 99, 105, 112, 104, 101, 114 });

                // Resize the array to the desired keysize. KeySize is in bits,
                // and Array.Resize wants the length in bytes.
                Array.Resize(ref cipherKey, symmetricAlgorithm.KeySize / 8);

                symmetricAlgorithm.Key = cipherKey;
            }

            return symmetricAlgorithm;
        }

        /// <summary>
        /// Open a properly configured <see cref="HMAC"/> conforming to the scheme
        /// identified by <paramref name="aeMac"/>.
        /// </summary>
        /// <param name="aeMac">The message authentication mode to open.</param>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <returns>
        /// An HMAC object with the proper key, or <c>null</c> on unknown algorithms.
        /// </returns>
        private static HMAC GetMac(AeMac aeMac, byte[] masterKey)
        {
            HMAC hmac;

            switch (aeMac)
            {
                case AeMac.HMACSHA256:
                    hmac = new HMACSHA256();
                    break;
                case AeMac.HMACSHA384:
                    hmac = new HMACSHA384();
                    break;
                default:
                    // An algorithm we don't understand
                    throw new CryptographicException();
            }

            // Instead of using the master key directly, derive a key for our chosen
            // HMAC algorithm based upon the master key.
            // Since the output size of the HMAC is the same as the ideal key size for
            // the HMAC, we can use the master key over a fixed input once to perform
            // NIST SP 800-108 5.1 (Counter Mode KDF):
            hmac.Key = masterKey;

            // i=1, Context=ASCII(MAC)
            byte[] newKey = hmac.ComputeHash(new byte[] { 1, 77, 65, 67 });

            hmac.Key = newKey;
            return hmac;
        }

        // A simple helper method to ensure that the offset (writePos) always moves
        // forward with new data.
        private static void Append(byte[] newData, byte[] combinedData, ref int writePos)
        {
            Buffer.BlockCopy(newData, 0, combinedData, writePos, newData.Length);
            writePos += newData.Length;
        }

        /// <summary>
        /// Compare the contents of two arrays in an amount of time which is only
        /// dependent on <paramref name="length"/>.
        /// </summary>
        /// <param name="a">An array to compare to <paramref name="b"/>.</param>
        /// <param name="aOffset">
        /// The starting position within <paramref name="a"/> for comparison.
        /// </param>
        /// <param name="b">An array to compare to <paramref name="a"/>.</param>
        /// <param name="bOffset">
        /// The starting position within <paramref name="b"/> for comparison.
        /// </param>
        /// <param name="length">
        /// The number of bytes to compare between <paramref name="a"/> and
        /// <paramref name="b"/>.</param>
        /// <returns>
        /// <c>true</c> if both <paramref name="a"/> and <paramref name="b"/> have
        /// sufficient length for the comparison and all of the applicable values are the
        /// same in both arrays; <c>false</c> otherwise.
        /// </returns>
        /// <remarks>
        /// An "insufficient data" <c>false</c> response can happen early, but otherwise
        /// a <c>true</c> or <c>false</c> response take the same amount of time.
        /// </remarks>
        [MethodImpl(MethodImplOptions.NoInlining | MethodImplOptions.NoOptimization)]
        private static bool CryptographicEquals(
            byte[] a,
            int aOffset,
            byte[] b,
            int bOffset,
            int length)
        {
            Debug.Assert(a != null);
            Debug.Assert(b != null);
            Debug.Assert(length >= 0);

            int result = 0;

            if (a.Length - aOffset < length || b.Length - bOffset < length)
            {
                return false;
            }

            unchecked
            {
                for (int i = 0; i < length; i++)
                {
                    // Bitwise-OR of subtraction has been found to have the most
                    // stable execution time.
                    //
                    // This cannot overflow because bytes are 1 byte in length, and
                    // result is 4 bytes.
                    // The OR propagates all set bytes, so the differences are only
                    // present in the lowest byte.
                    result = result | (a[i + aOffset] - b[i + bOffset]);
                }
            }

            return result == 0;
        }
    }
}
```
