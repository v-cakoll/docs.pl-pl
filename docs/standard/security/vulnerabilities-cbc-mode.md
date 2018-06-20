---
title: Luki w zabezpieczeniach chronometrażu z trybie CBC odszyfrowywania symetrycznego za pomocą wypełnienia
description: Dowiedz się, jak wykrywanie i usuwanie luk w zabezpieczeniach chronometrażu z odszyfrowanie symetryczne tryb Cipher-Block Chaining (CBC) za pomocą wypełnienia.
ms.date: 06/12/2018
author: blowdart
ms.author: mairaw
ms.openlocfilehash: 26f4d19f591ac02d792bebbd648e90b07d84de56
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208516"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a>Luki w zabezpieczeniach chronometrażu z trybie CBC odszyfrowywania symetrycznego za pomocą wypełnienia

Firma Microsoft uzna, że nie jest już bezpieczne odszyfrowanie danych zaszyfrowanych w trybie Cipher-Block Chaining (CBC) szyfrowania symetrycznego, gdy zweryfikowania dopełnienie zostało zastosowane bez pierwszy zapewniania integralności tekstu szyfrowanego, z wyjątkiem bardzo szczegółowej okoliczności. Tej oceny jest oparta na aktualnie znane badań kryptograficznych. 

## <a name="introduction"></a>Wprowadzenie

Atak oracle uzupełnienie jest typem ataku przeciwko zaszyfrowanych danych, który umożliwia osobie atakującej na odszyfrowywanie zawartości danych, bez uprzedniego uzyskania informacji o kluczu.

Oracle odnosi się do "Powiadom" które daje atakująca informacje są one wykonywania akcji jest prawidłowa lub nie. Wyobraź sobie odtwarzanie tablicę lub kart gry z elementem podrzędnym. Po jej krój podświetlony z dużą uśmiech ponieważ Agnieszka przebywa o dokonanie dobry ruch, który jest oracle. Jako przeciwnika, można to oracle odpowiednio zaplanować przejście dalej.

Uzupełnienie jest kryptograficznych określonego wyrażenia. Niektóre szyfrów, które są algorytmy używane do szyfrowania danych, działają na bloki danych, gdzie każdy blok jest o stałym rozmiarze. Jeśli dane, które chcesz zaszyfrować nie ma właściwego rozmiaru w celu wypełnienia bloki, danych jest wypełniane, dopóki nie robi. Wiele form uzupełnienia wymagają tego uzupełnienia zawsze być obecne, nawet jeśli oryginalny wprowadzono właściwego rozmiaru. Dzięki temu uzupełnienia zawsze można bezpiecznie usunąć po odszyfrowywania.

Zestawienie dwie rzeczy, wdrożenia oprogramowania z oracle dopełnienie wykazuje, czy odszyfrowane dane mają prawidłowy dopełnienie. Programu oracle można coś najprostszą zwracanie wartości informacją "Nieprawidłowy dopełnienie" lub coś bardziej skomplikowany, takich jak widoczny różnych czasu przetwarzania prawidłowy blok przeciwieństwie nieprawidłowy blok.

Szyfry opartej na blokach ma inna właściwość o nazwie tryb, który określa relacji danych w pierwszym bloku danych w drugim bloku, i tak dalej. Jeden z trybów najczęściej używane jest CBC. CBC wprowadza początkowej blok losowych, znane jako inicjowania wektora (IV) i łączy poprzedniego bloku z wynikiem statycznych szyfrowania, aby była w taki sposób, że szyfrowanie ten sam komunikat z tym samym kluczem zawsze nie tworzy tych samych zaszyfrowanych danych wyjściowych.

Osobie atakującej wykorzystanie programu oracle dopełnienie, w połączeniu z struktury danych CBC, do wysyłania wiadomości nieco zmienione do kodu, który ujawnia programu oracle i zachować wysyłanie danych do czasu programu oracle dowie się, dane są poprawne. Osoba atakująca może odszyfrować wiadomości po bicie, z tej odpowiedzi.

Nowoczesne komputera sieci są takie wysokiej jakości, że osoba atakująca może wykryć bardzo małe (mniej niż 0,1 ms) różnice w wykonywania czasu w systemach zdalnych. Aplikacje, które są przy założeniu, że pomyślnie odszyfrowywania tylko zdarzyć, gdy dane nie został zmieniony przez niepowołane może być narażony na ataki z narzędzia, które są przeznaczone do przestrzegania różnice w odszyfrowywania zakończone powodzeniem i niepowodzeniem. Ta różnica czasu może być bardziej znaczących w niektórych językach lub biblioteki niż inne, teraz uważa się, że jest to praktyczne zagrożenie dla wszystkich języków i bibliotek, gdy aplikacji odpowiedzi na błędy jest brana pod uwagę.

Atak polega na możliwość zmieniania zaszyfrowanych danych i testowania wynik z programu oracle. Jedynym sposobem, aby ograniczyć pełni ataku jest wykrywa zmiany do zaszyfrowanych danych i odmówić wykonywać w niej żadnych akcji. Standardowy sposób, w tym celu jest utworzenie podpisu dla danych i sprawdź poprawność tego podpisu, przed wykonaniem jakichkolwiek operacji. Podpis musi być możliwe do zweryfikowania, nie można utworzyć przez osobę atakującą, w przeciwnym razie ich czy zmienić zaszyfrowane dane, a następnie obliczyć podpisu nowy, oparty na zmienione dane. Jeden typ wspólnego z odpowiednim podpisem nosi nazwę kod uwierzytelniania wiadomości z kluczem skrótu (HMAC). HMAC różni się od sumy kontrolnej, że trwa klucz tajny, znane tylko osoby HMAC generująca lub osoby jej skuteczność. Bez posiadaniu klucza nie można utworzyć poprawne HMAC. Podczas odbierania danych, należy wykonać zaszyfrowane dane, niezależnie obliczeniowe HMAC przy użyciu klucza tajnego, możesz i nadawcy udziału, a następnie porównaj HMAC one wysyłane za jedną należy obliczyć. To porównanie musi być stałą czasu, w przeciwnym razie dodaniu innego oracle wykrywalny, co pozwala na inny rodzaj ataku.

Podsumowując do używania dopełniane szyfrów bloku CBC bezpiecznie, należy połączyć je z HMAC (lub innego sprawdzania integralności danych), który weryfikacji przy użyciu porównanie stałej czasu przed przystąpieniem do odszyfrowania danych. Ponieważ wszystkie komunikaty zmieniony zająć jednocześnie Kwota do tworzenia odpowiedzi, nie będzie mógł ataku.

## <a name="who-is-vulnerable"></a>Kto jest zagrożony

Ta luka w zabezpieczeniach dotyczy zarządzane i natywne aplikacje, które wykonują własne szyfrowanie i odszyfrowywanie. Obejmuje to, na przykład:

- Aplikacja, która powoduje zaszyfrowanie pliku cookie do nowszej odszyfrowywania na serwerze.
- Aplikacja bazy danych, która zapewnia możliwość przez użytkowników do wstawiania danych do tabeli, w których kolumny są później odszyfrować.
- Aplikacja transferu danych, która korzysta z szyfrowania do ochrony danych podczas przesyłania przy użyciu klucza wspólnego.
- Aplikacja, która szyfruje i odszyfrowuje wiadomości "od wewnątrz" tunelu TLS.

Należy pamiętać, że używają wyłącznie protokołu TLS może nie chronią w tych scenariuszach.

Usterce aplikacji:

- Odszyfrowuje dane w trybie CBC szyfrowania z trybem dopełnienie podlegające weryfikacji, takie jak PKCS #7 lub ANSI X.923.
- Wykonuje odszyfrowywanie bez o wykonywane sprawdzanie integralności (za pośrednictwem MAC lub asymetrycznego podpisu cyfrowego).

Dotyczy to również aplikacje, rozszerzający abstrakcje w górnej części tych podstawowych, takich jak struktury EnvelopedData składni wiadomości kryptograficznych (PKCS #7/CMS).

## <a name="related-areas-of-concern"></a>Powiązane obszary zainteresowania

Badania spowodowało Microsoft w celu dalszego zajmującym CBC wiadomości, które są dopełniane przy ISO 10126-równoważne wypełnienia podczas wiadomości ma strukturę stopki dobrze znanego lub prognozowanych. Na przykład zawartość przygotowany zgodnie z regułami W3C XML szyfrowania składni i przetwarzania zalecenie (xmlenc EncryptedXml). Gdy wskazówki W3C do podpisania wiadomości, a następnie szyfrować uznano za właściwe, w tym czasie, firma Microsoft zaleca teraz zawsze podczas szyfrowania to znak.

Deweloperzy aplikacji powinien zawsze mieć sprawdzanie możliwości zastosowania danego klucza asymetrycznego podpisu, mając na uwadze, ponieważ nie ma żadnych relacji zaufania związane między klucza asymetrycznego i dowolnego komunikatu.

## <a name="details"></a>Szczegóły

W przeszłości ma zostać konsensu, które są ważne do szyfrowania i uwierzytelniania ważnych danych, przy użyciu środków, takich jak HMAC lub RSA podpisów. Jednak było w niej mniej wyraźnych wskazówek sposobów sekwencji operacji szyfrowania i uwierzytelniania. Z powodu usterki szczegółowo opisane w tym artykule wskazówkami firmy Microsoft jest teraz zawsze używaj modelu "szyfrowania następnie znaku". Oznacza to najpierw szyfrowania danych przy użyciu klucza symetrycznego, a następnie obliczeniowego MAC lub podpisu asymetrycznego za pośrednictwem tekstu szyfrowanego (zaszyfrowanych danych). Podczas deszyfrowania danych, należy przeprowadzić odwrotnej. Najpierw upewnij się, MAC lub podpis tekstu szyfrowanego, a następnie go odszyfrować.

Klasa jest ogólnie znana jako "padding ataków oracle" znane istnieje ponad 10 lat luk w zabezpieczeniach. Te luki w zabezpieczeniach osoba atakująca na odszyfrowanie danych zaszyfrowanych przez blok symetryczne algorytmy, takie jak AES i 3DES, przy użyciu nie więcej niż 4096 prób na blok danych. Wprowadź te luki w zabezpieczeniach korzystanie z faktu, że zablokowanie szyfrów najczęściej używanych z danymi weryfikowalny dopełnienie na końcu. Okazało się, że jeśli osoba atakująca może manipulować tekstu szyfrowanego i sprawdzić, czy o naruszeniu spowodował błąd w formacie wypełnienia na końcu, osoba atakująca może odszyfrować danych.

Początkowo praktyczne ataków znajdowały się na usługami zwracającymi kody błędów różnych oparte na czy dopełnienie była prawidłowa, taka jak luki w zabezpieczeniach ASP.NET [MS10-070](https://technet.microsoft.com/library/security/ms10-070.aspx). Jednak firma Microsoft teraz uzna, że jest to możliwe przeprowadzenie podobne ataki za pomocą tylko różnice czasu między przetwarzania dopełnienie prawidłowe oraz nieprawidłowe.

Pod warunkiem, że podpis wykorzystuje schemat szyfrowania i weryfikacja podpisu jest wykonywane z stałym środowiska uruchomieniowego dla podanej długości danych (niezależnie od zawartości), bez emitowanie informacji, które można sprawdzić spójność danych Osoba atakująca za pośrednictwem [kanału po stronie](https://en.wikipedia.org/wiki/Side-channel_attack). Ponieważ sprawdzania integralności odrzuca komunikaty zmodyfikowany, skuteczność została osłabiona zagrożeń oracle dopełnienia.

## <a name="guidance"></a>Wskazówki

Najpierw i, firma Microsoft zaleca musi być przekazywane za pośrednictwem zabezpieczeń TLS (Transport Layer), następnika do Secure Sockets Layer (SSL) zawierający poufności danych.

Następnie analizować aplikacji:

- Dowiedz się dokładnie szyfrowania, jaką wykonujesz i jakie szyfrowanie jest świadczona przez platform i interfejsów API używasz.
- Się upewnić, że każdy użycia w każdej warstwie symetrycznego [algorytmu szyfrowania bloku](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), takie jak AES i 3DES w trybie CBC zawierają stosowania sprawdzania integralności danych klucze tajne (podpisu asymetrycznego HMAC lub zmienić tryb szyfrowania do [uwierzytelniony szyfrowania](https://en.wikipedia.org/wiki/Authenticated_encryption) trybu (AE), takim jak GCM lub CCM).

W oparciu o bieżący badań, ogólnie uważa się, że w przypadku uwierzytelnianie i szyfrowanie kroki są wykonywane niezależnie dla trybów AE bez szyfrowania, uwierzytelniania szyfrowanego (szyfrowanie następnie Podpisz) jest najlepszą opcją ogólne. Niestety nie są bez pasującego poprawną odpowiedź na kryptografii i jak ukierunkowanej poradę professional cryptographer nie jest to generalizacji.

Aplikacje, które można zmienić ich format wiadomości, jednak wykonywać nieuwierzytelnione odszyfrowywania CBC zaleca się spróbuj zastosować środki zaradcze, takich jak:

- Odszyfrowywania bez możliwości odszyfrowujący weryfikacji lub usunąć uzupełnienie:
  - Wszelkie uzupełnienia, która została zastosowana nadal musi zostać usunięte lub zignorowane, przenoszenia obciążeń w aplikacji.
  - Korzyścią jest to, że dopełnienie weryfikacji i usuwania mogą być włączone w innych logikę weryfikacji danych aplikacji. Dopełnienie weryfikacji i weryfikacja danych mogą być przeprowadzane w czasie stałej, ograniczono zagrożenia.
  - Ponieważ interpretacji wypełnienia zmienia długość komunikatu postrzegana, może nadal być informacji wyemitowanego z tej metody.
- Zmień tryb uzupełniania odszyfrowywania ISO10126:
  - Dopełnienie odszyfrowywania ISO10126 jest zgodny z zarówno wypełnienie PKCS7 i wypełnienie ANSIX923.
  - Zmienianie trybu ogranicza wiedzy oracle uzupełnienie do 1 bajt zamiast całego bloku. Jeśli zawartość ma dobrze znanego stopki, takich jak zamykającego elementu XML pokrewne ataków jednak na ataki pozostałej części wiadomości.
  - To również nie uniemożliwia odzyskiwanie zwykłego tekstu w sytuacji, gdy osoba atakująca można przekształcić tego samego zwykły tekst do zaszyfrowania wiele razy z przesunięciem inny komunikat.
- Brama obliczania wywołania odszyfrowywania Rozmoczenie sygnału czasu:
  - Obliczenia czasu blokady musi mieć co najmniej przekracza maksymalną ilość czasu, który wykonać operacji odszyfrowywania dla żadnego z segmentów danych zawierający dopełnienia.
  - Obliczenia czas należy przeprowadzić zgodnie z instrukcjami podanymi w [pobierania sygnatur czasowych wysokiej rozdzielczości](https://msdn.microsoft.com/library/windows/desktop/dn55340.aspx), nie za pomocą <xref:System.Environment.TickCount?displayProperty=nameWithType> (może ulec roll-over/przepełnienie) lub usunięcie dwóch systemu sygnatur czasowych (zgodnie z korekty NTP błędy).
  - Obliczenia czas musi być tym operacji odszyfrowywania wszystkich potencjalnych wyjątków w tym zarządzane lub aplikacje w języku C++ nie tylko. dopełniane na końcu.
  - Jeśli powodzenie lub niepowodzenie odnalezieniu jeszcze bramy chronometrażu musi zwracać błąd, po jego wygaśnięciu.
- Usługi, które działają nieuwierzytelnione odszyfrowywania powinien mieć monitorowania w celu wykrycia, czy powódź "nieprawidłowe" komunikatów do trybu za pośrednictwem.
  - Przy tym pamiętać, że ten sygnał prowadzi zarówno fałszywych alarmów (legalnie uszkodzone dane), jak i fałszywych wyników negatywnych (rozkładanie ataków za pośrednictwem wystarczająco dużo czasu uniknięcia wykrywania).

## <a name="finding-vulnerable-code---native-applications"></a>Wyszukiwanie kodu luki w zabezpieczeniach - natywnych aplikacji

Dla programów, które utworzono przy użyciu kryptografii systemu Windows: Biblioteka nowej generacji (CNG):

- Wywołanie odszyfrowywania ma na celu [BCryptDecrypt](https://msdn.microsoft.com/library/windows/desktop/aa375391.aspx), określania `BCRYPT_BLOCK_PADDING` flagi.
- Dojście klucza została zainicjowana przez wywołanie metody [BCryptSetProperty](https://msdn.microsoft.com/library/windows/desktop/aa375504.aspx) z [BCRYPT_CHAINING_MODE](https://msdn.microsoft.com/library/windows/desktop/aa376211.aspx#BCRYPT_CHAINING_MODE) ustawioną `BCRYPT_CHAIN_MODE_CBC`.
  - Ponieważ `BCRYPT_CHAIN_MODE_CBC` jest ustawienie domyślne, których to dotyczy kodu nie może przypisać wszystkie wartości `BCRYPT_CHAINING_MODE`.

Dla programów utworzono przy użyciu starszej kryptograficznego interfejsu API systemu Windows:

- Wywołanie odszyfrowywania ma na celu [CryptDecrypt](https://msdn.microsoft.com/library/windows/desktop/aa379913.aspx) z `Final=TRUE`.
- Dojście klucza została zainicjowana przez wywołanie metody [CryptSetKeyParam](https://msdn.microsoft.com/library/windows/desktop/aa380272.aspx) z [KP_MODE](https://msdn.microsoft.com/library/windows/desktop/aa379949.aspx#KP_MODE) ustawioną `CRYPT_MODE_CBC`.
  - Ponieważ `CRYPT_MODE_CBC` jest ustawienie domyślne, których to dotyczy kodu nie może przypisać wszystkie wartości `KP_MODE`.

## <a name="finding-vulnerable-code---managed-applications"></a>Znajdowanie niebezpieczny kod - zarządzanych aplikacji

- Wywołanie odszyfrowywania ma na celu <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> lub <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> metody <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.
  - Dostępne są następujące typy pochodne w ramach programu .NET, ale mogą również obejmować typów innych firm:
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
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> Ustawiono właściwość <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>, lub <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.
  - Ponieważ <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> jest ustawienie domyślne, których to dotyczy kodu może nigdy nie przypisano <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> właściwości.
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> Ustawiono właściwość <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType>
  - Ponieważ <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> jest ustawienie domyślne, których to dotyczy kodu może nigdy nie przypisano <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> właściwości.

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a>Wyszukiwanie kodu luki w zabezpieczeniach - składni wiadomości kryptograficznych

Wiadomość CMS EnvelopedData nieuwierzytelnione którego zaszyfrowaną zawartość używa trybu CBC AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), (1.3.14.3.2.7) DES, 3DES (1.2.840.113549.3.7) lub RC2 (1.2.840.113549.3.2) jest narażony, jak również w wiadomości w trybie CBC przy użyciu innych algorytmów szyfrowania bloku.

Gdy szyfrów strumienia nie są podatne na tę lukę w zabezpieczeniach określonego, firma Microsoft zaleca zawsze uwierzytelnianie danych za pośrednictwem sprawdzania wartości ContentEncryptionAlgorithm.

Dla zarządzanych aplikacji EnvelopedData CMS, obiektów blob może być wykryte jako żadnej wartości, który jest przekazywany do <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.

Dla natywnych aplikacji mogą być wykrywane CMS EnvelopedData obiektu blob jako podanie do uchwytu CMS za pomocą dowolnej wartości [CryptMsgUpdate](https://msdn.microsoft.com/library/windows/desktop/aa380231.aspx) których wynikowa [CMSG_TYPE_PARAM](https://msdn.microsoft.com/library/windows/desktop/aa380227.aspx) jest `CMSG_ENVELOPED` i/lub dojście CMS później wysyłane `CMSG_CTRL_DECRYPT` instrukcji za pomocą [CryptMsgControl](https://msdn.microsoft.com/library/windows/desktop/aa380220.aspx).

## <a name="vulnerable-code-example---managed"></a>Przykład kodu luki w zabezpieczeniach — zarządzane

Ta metoda odczytuje plik cookie i odszyfrowuje ją i sprawdzanie integralności danych nie jest widoczny. W związku z tym zawartość pliku cookie, który jest odczytywany przez tę metodę można ataku przez użytkownika, który otrzymał go, lub każda osoba atakująca, która uzyskała wartość zaszyfrowanego pliku cookie.

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

## <a name="example-code-following-recommended-practices---managed"></a>Przykład kodu następujących zalecanych rozwiązań - zarządzany

Następujący przykładowy kod używa komunikatu niestandardowym formacie

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

gdzie `cipher_algorithm_id` i `hmac_algorithm_id` algorytm identyfikatory są (niestandardowy) reprezentacje tych algorytmów lokalnego aplikacji. Te identyfikatory może być uzasadniona w innych częściach z istniejącego protokołu obsługi zamiast jako systemu od zera połączonych strumienia bajtów.

W tym przykładzie również korzysta z jednego klucza głównego pochodzić zarówno klucz szyfrowania, jak i klucz HMAC. To jest dostępna zarówno jako udogodnienie dla Włączanie aplikacji z kluczem pojedynczo do aplikacji z kluczem procesory i zachęca utrzymywanie dwa klucze, jak różne wartości. Gwarantuje dalsze, nie można pobrać klucza HMAC i klucz szyfrowania poza synchronizacji.

W tym przykładzie nie akceptuje <xref:System.IO.Stream> do szyfrowania lub odszyfrowywania. Bieżące dane formatu sprawia, że jeden przebieg szyfrowania trudne ponieważ `hmac_tag` wartość poprzedza tekstu szyfrowanego. Jednak ten format została wybrana, ponieważ utrzymuje wszystkich elementów o stałym rozmiarze na początku, aby zachować analizator prostsze. Z tego formatu danych odszyfrowywania jeden przebieg jest możliwe, że implementujący jest cautioned wywołać GetHashAndReset i sprawdź wynik przed wywołaniem metody TransformFinalBlock. Jeśli szyfrowanie przesyłania strumieniowego odgrywa ważną rolę, inny tryb AE mogą być wymagane.

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
