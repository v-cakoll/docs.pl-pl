---
title: Luka w zabezpieczeniach odszyfrowywania CBC
description: Dowiedz się, jak wykrywać i ograniczać luki w zabezpieczeniach dotyczące chronometrażu przy użyciu szyfrowania symetrycznego trybu łańcucha (CBC).
ms.date: 06/12/2018
author: blowdart
ms.author: mairaw
ms.openlocfilehash: 1d570cf3da197e7af5c1a1ab4e4df0d21f2cb2d7
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347233"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a>Luki w zabezpieczeniach chronometrażu z odszyfrowywaniem symetrycznym w trybie CBC przy użyciu uzupełnienia

Firma Microsoft uważa, że nie jest już bezpiecznie odszyfrowywać dane zaszyfrowane przy użyciu trybu szyfr-blocking (CBC) szyfrowania symetrycznego, gdy stosowane jest dopełnienie, bez uprzedniego zapewnienia integralności tekstu szyfrowanego, z wyjątkiem bardzo szczególnych rodzin. Jest to orzeczenie oparte na aktualnie znanych badaniach kryptograficznych. 

## <a name="introduction"></a>Wprowadzenie

Zapełnienie ataku Oracle jest typem ataków na zaszyfrowane dane, które umożliwiają atakującemu odszyfrowanie zawartości danych bez znajomości klucza.

Firma Oracle odnosi się do "powiedzieć", który zapewnia atakującemu informacje o tym, czy wykonywana akcja jest poprawna, czy nie. Wyobraź sobie, że gra plansza lub karta jest połączona z elementem podrzędnym. Gdy jej czołowa lampka ma duży uśmiech, ponieważ uzna, że jest to dobry ruch, to jest Oracle. Jako przeciwnik może użyć tego programu Oracle do zaplanowania odpowiednio następnego przejścia.

Uzupełnienie jest określonym warunkiem kryptograficznym. Niektóre szyfry, które są algorytmami używanymi do szyfrowania danych, działają na blokach danych, w których każdy blok ma stały rozmiar. Jeśli dane, które mają zostać zaszyfrowane, nie są odpowiednim rozmiarem do wypełnienia bloków, dane są uzupełniane do momentu, w którym się nie robi. Wiele form uzupełniania wymaga, aby uzupełnienie było zawsze obecne, nawet jeśli oryginalne dane wejściowe miały prawidłowy rozmiar. Dzięki temu uzupełnianie będzie zawsze bezpiecznie usuwane podczas odszyfrowywania.

Jednoczesne umieszczenie obu tych elementów spowoduje, że implementacja oprogramowania z nieuzupełnieniem programu Oracle pokazuje, czy odszyfrowane dane mają prawidłowe uzupełnienie. Oracle może być coś prostej, ponieważ zwraca wartość "nieprawidłowe uzupełnienie" lub coś bardziej skomplikowanego, jak przetwarzać prawidłowy blok, w przeciwieństwie do nieprawidłowego bloku.

Szyfry oparte na blokach mają inną właściwość o nazwie Mode, która określa relację danych w pierwszym bloku z danymi w drugim bloku itd. Jednym z najczęściej używanych trybów jest CBC. CBC wprowadza początkowy losowy blok, znany jako wektor inicjujący (IV) i łączy poprzedni blok z wynikiem statycznego szyfrowania, aby uniemożliwić mu szyfrowanie tego samego komunikatu z tym samym kluczem, nie zawsze generują te same zaszyfrowane dane wyjściowe.

Osoba atakująca może korzystać z uzupełniania oprogramowania Oracle, w połączeniu z CBC danych, w celu wysyłania nieco zmienionych komunikatów do kodu, który ujawnia oprogramowanie Oracle, a także do wysyłania danych do momentu, gdy firma Oracle poinformuje ich, że dane są poprawne. Z tej odpowiedzi osoba atakująca może odszyfrować bajt komunikatu według bajtu.

Nowoczesne sieci komputerowe mają taką wysoką jakość, którą atakujący może wykryć bardzo małe (mniej niż 0,1 ms) różnice w czasie wykonywania w systemach zdalnych. Aplikacje, które zakładają, że pomyślne odszyfrowywanie może wystąpić tylko wtedy, gdy dane nie zostały naruszone, mogą być narażone na ataki z narzędzi, które są przeznaczone do zaobserwowania różnic w przypadku pomyślnego i nieudanego odszyfrowania. Chociaż różnica czasu może być bardziej znacząca w niektórych językach lub bibliotekach niż inne, uważa się, że jest to praktyczne zagrożenie dla wszystkich języków i bibliotek, gdy odpowiedź aplikacji do awarii jest brana pod uwagę.

Ten atak polega na możliwości zmiany zaszyfrowanych danych i przetestowania wyniku przy użyciu programu Oracle. Jedynym sposobem na całkowite ograniczenie ataku jest wykrycie zmian zaszyfrowanych danych i odrzucenie wykonywania jakichkolwiek działań na nim. Standardowy sposób to utworzenie podpisu dla danych i zweryfikowanie podpisu przed wykonaniem jakiejkolwiek operacji. Podpis musi być możliwy do zweryfikowania, nie może być utworzony przez osobę atakującą, w przeciwnym razie zmienia zaszyfrowane dane, a następnie oblicza nowy podpis na podstawie zmienionych danych. Jeden wspólny typ odpowiedniej sygnatury jest znany jako kod uwierzytelniania wiadomości podwyższego poziomu (HMAC). HMAC różni się od sumy kontrolnej w tym, że przyjmuje klucz tajny znany tylko osobie wytwarzającej kod HMAC i osobie sprawdzającej ją. Bez posiadania klucza nie można utworzyć poprawnego algorytmu HMAC. Po otrzymaniu danych można wykonać zaszyfrowane dane, niezależnie od obliczenia algorytmu HMAC przy użyciu klucza tajnego i udziału nadawcy, a następnie porównać kod HMAC, który został wysłany na obliczony. To porównanie musi być stałą godziną, w przeciwnym razie dodaliśmy kolejną wykrywalną wersję Oracle, co pozwala na atak innego typu.

Podsumowując, aby bezpiecznie korzystać z uzupełnionych szyfrów CBC Block, należy połączyć je z HMAC (lub innym sprawdzaniem integralności danych), które są weryfikowane przy użyciu stałego porównania czasu przed próbą odszyfrowania danych. Ponieważ wszystkie zmienione komunikaty mają ten sam czas na wygenerowanie odpowiedzi, atak jest nieautoryzowany.

## <a name="who-is-vulnerable"></a>Kto jest narażony

Ta luka w zabezpieczeniach dotyczy zarówno aplikacji zarządzanych, jak i natywnych, które wykonują własne szyfrowanie i odszyfrowywanie. Dotyczy to na przykład:

- Aplikacja, która szyfruje plik cookie na potrzeby późniejszego odszyfrowywania na serwerze.
- Aplikacja bazy danych, która zapewnia użytkownikom możliwość wstawiania danych do tabeli, której kolumny są później odszyfrowywane.
- Aplikacja do transferu danych, która opiera się na szyfrowaniu przy użyciu klucza współużytkowanego do ochrony przesyłanych danych.
- Aplikacja, która szyfruje i odszyfrowuje komunikaty "wewnątrz" tunelu TLS.

Należy pamiętać, że użycie protokołu TLS sama może nie chronić w tych scenariuszach.

Aplikacja podatna na ataki:

- Odszyfrowuje dane przy użyciu trybu szyfru CBC z możliwym do sprawdzenia trybem uzupełniania, takim jak PKCS # 7 lub ANSI X. 923.
- Wykonuje odszyfrowywanie bez wykonywania kontroli integralności danych (za pośrednictwem komputera MAC lub asymetrycznego podpisu cyfrowego).

Dotyczy to również aplikacji utworzonych na podstawie abstrakcji na podstawie tych elementów pierwotnych, takich jak struktura EnvelopedData składni wiadomości kryptograficznych (PKCS # 7/CMS).

## <a name="related-areas-of-concern"></a>Powiązane obszary problemu

Badania przeprowadziły do tego, że firma Microsoft może być bardziej zainteresowani komunikatami CBC, które zostały uzupełnione o przypełnienie ISO 10126, gdy komunikat ma dobrze znaną lub przewidywalną strukturę stopek. Na przykład zawartość przygotowana zgodnie z regułami składni szyfrowania XML i zalecenia dotyczące przetwarzania (xmlenc, EncryptedXml). Chociaż wskazówki dotyczące W3C podpisywania wiadomości są uważane za odpowiednie, firma Microsoft zaleca, aby zawsze przeprowadzać szyfrowanie i podpisywanie.

Deweloperzy aplikacji powinni zawsze mieć pewność, że sprawdzają możliwość zastosowania klucza podpisu asymetrycznego, ponieważ nie istnieje relacja zaufania między kluczem asymetrycznym a dowolnym komunikatem.

## <a name="details"></a>Szczegóły

W przeszłości nastąpiło jednomyślne zaszyfrowanie i uwierzytelnienie ważnych danych przy użyciu takich metod jak HMAC lub sygnatury RSA. Istnieje jednak mniej jasne wskazówki dotyczące sekwencji operacji szyfrowania i uwierzytelniania. Ze względu na lukę w zabezpieczeniach w tym artykule wskazówki firmy Microsoft mają teraz zawsze używać odmian "Szyfruj-and-Sign". Oznacza to, że najpierw szyfruje dane przy użyciu klucza symetrycznego, a następnie oblicza sygnaturę adresu MAC lub asymetrycznego w postaci tekstu szyfrowanego (dane zaszyfrowane). Podczas odszyfrowywania danych wykonaj odwracanie. Najpierw Potwierdź adres MAC lub podpis tekstu szyfrowanego, a następnie Odszyfruj go.

Wiadomo, że klasa luk w zabezpieczeniach, znana jako "dopełnienie ataków Oracle", już istnieje przez ponad 10 lat. Luki w zabezpieczeniach umożliwiają atakującemu odszyfrowanie danych szyfrowanych przez algorytmy bloku symetrycznego, takie jak AES i 3DES, przy użyciu nie więcej niż 4096 prób na blok danych. Te luki w zabezpieczeniach korzystają z faktu, że Szyfry blokowe są najczęściej używane z możliwymi do zweryfikowania danymi na końcu. Okazało się, że jeśli osoba atakująca może zmodyfikować szyfrowanie i dowiedzieć się, czy manipulowanie powodowało błąd w formacie uzupełnienia na końcu, osoba atakująca może odszyfrować dane.

Początkowo praktyczne ataki dotyczyły usług, które zwracają różne kody błędów w oparciu o to, czy dopełnienie było prawidłowe, takie jak [ASP.NET luk w](/security-updates/SecurityBulletins/2010/ms10-070)zabezpieczeniach. Jednak firma Microsoft uważa, że jest to praktyczne, aby przeprowadzić podobne ataki, używając tylko różnic czasu między przetwarzaniem prawidłowym i nieprawidłowym uzupełnieniem.

Pod warunkiem, że schemat szyfrowania używa podpisu i że weryfikacja podpisu jest wykonywana ze stałym środowiskiem uruchomieniowym dla danej długości danych (niezależnie od zawartości), integralność danych można zweryfikować bez emitowania jakichkolwiek informacji do osoby atakującej za pośrednictwem [kanału bocznego](https://en.wikipedia.org/wiki/Side-channel_attack). Ze względu na to, że sprawdzanie integralności odrzuci wszystkie naruszone komunikaty, dopełnienie zagrożeń firmy Oracle zostało skorygowane.

## <a name="guidance"></a>Wskazówki

Przede wszystkim firma Microsoft zaleca, aby wszystkie dane, które mają wymagania dotyczące poufności, były przesyłane za pośrednictwem Transport Layer Security (TLS), następnika SSL (SSL).

Następnie Przeanalizuj swoją aplikację w:

- Zapoznaj się z precyzyjnymi informacjami o debugowanym szyfrowaniu oraz o tym, jakie szyfrowanie jest zapewniane przez używane platformy i interfejsy API.
- Należy upewnić się, że każde użycie w każdej warstwie [algorytmu symetrycznego szyfrowania bloku](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), takie jak AES i 3DES, w trybie CBC obejmuje użycie kontroli integralności danych z tajnym kluczem (w postaci nieasymetrycznego, algorytmu HMAC lub zmiany trybu szyfrowania na [uwierzytelnianie uwierzytelnione](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE), np. GCM lub CCM).

W oparciu o bieżące badania ogólnie uważa się, że po wykonaniu czynności związanych z uwierzytelnianiem i szyfrowaniem niezależnie od trybu nieae, uwierzytelnianie tekstu szyfrowanego (szyfrowania i podpisywania) jest najlepszą opcją ogólną. Nie ma jednak żadnej prawidłowej odpowiedzi na kryptografię, a to uogólnienie nie jest tak dobre jak ukierunkowane porady z cryptographer Professional.

Aplikacje, które nie mogą zmienić formatu komunikatów, ale mogą wykonać nieuwierzytelnione odszyfrowywanie CBC, aby próbować uwzględnić środki zaradcze, takie jak:

- Odszyfruj bez zezwalania na odszyfrowanie, aby zweryfikować lub usunąć uzupełnienie:
  - Wszelkie uzupełnienia, które zostały zastosowane nadal muszą zostać usunięte lub zignorowane, przenosisz obciążenie do aplikacji.
  - Korzyść polega na tym, że weryfikacja uzupełniania i usunięcie może być włączone do innej logiki weryfikacji danych aplikacji. Jeśli weryfikacja uzupełniania i weryfikacja danych można wykonać w stałym czasie, zagrożenie zostanie zmniejszone.
  - Ponieważ interpretacja uzupełniania zmienia długość komunikatu, nadal mogą być emitowane informacje o chronometrażu.
- Zmień tryb uzupełniania odszyfrowywania na ISO10126:
  - Uzupełnienie odszyfrowywania ISO10126 jest zgodne z uzupełnieniem szyfrowania i ANSIX923 szyfrowaniem.
  - Zmiana trybu zmniejsza uzupełnianie wiedzy Oracle do 1 bajt zamiast całego bloku. Jeśli jednak zawartość ma dobrze znaną stopkę, taką jak zamykający element XML, powiązane ataki mogą nadal zaatakować resztę wiadomości.
  - Uniemożliwia to również odzyskiwanie zwykłego tekstu w sytuacjach, gdy atakujący może przekształcić ten sam tekst w taki sposób, aby był szyfrowany wielokrotnie przy użyciu innego przesunięcia komunikatów.
- Ocenianie wywołania odszyfrowania w celu przeprowadzenia rozgłaszania sygnału czasu:
  - Obliczenie czasu wstrzymania musi mieć wartość minimalną przekraczającą maksymalną ilość czasu, jaką może wykonać operacja odszyfrowywania dla dowolnego segmentu danych zawierającego uzupełnienie.
  - Obliczenia czasu powinny odbywać się zgodnie ze wskazówkami dotyczącymi [uzyskiwania sygnatur czasowych o wysokiej rozdzielczości](/windows/desktop/sysinfo/acquiring-high-resolution-time-stamps), a nie za pomocą <xref:System.Environment.TickCount?displayProperty=nameWithType> (podlegają przewróceniu/przepełnieniu) lub odejmowania dwóch sygnatur czasowych systemu (z zastrzeżeniem błędów dopasowania NTP).
  - Obliczenia czasu muszą uwzględniać operacje odszyfrowywania, w tym wszystkie potencjalne wyjątki w zarządzanych lub aplikacjach C++ , a nie tylko na końcu.
  - Jeśli jeszcze nie określono sukcesu lub niepowodzenia, Brama czasu musi zwrócić błąd po wygaśnięciu.
- Usługi, które wykonują nieuwierzytelnione odszyfrowywanie, powinny mieć monitorowanie w celu wykrycia, że pozostała część komunikatów "nieprawidłowe" została przeprowadzona.
  - Należy pamiętać, że ten sygnał obejmuje zarówno fałszywie dodatnie (dane uszkodzone), jak i fałszywe negatywne (rozproszenie ataku w wystarczająco długim czasie w celu uniknięcia wykrywania).

## <a name="finding-vulnerable-code---native-applications"></a>Znajdowanie zagrożonych aplikacji natywnych kodu

W przypadku programów utworzonych w oparciu o bibliotekę kryptografii systemu Windows: nowej generacji (CNG):

- Wywołanie odszyfrowywania to [BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt), określając flagę `BCRYPT_BLOCK_PADDING`.
- Obsługa klucza została zainicjowana przez wywołanie [BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty) z ustawionym na `BCRYPT_CHAIN_MODE_CBC`[BCRYPT_CHAINING_MODE](/windows/desktop/SecCNG/cng-property-identifiers#BCRYPT_CHAINING_MODE) .
  - Ponieważ `BCRYPT_CHAIN_MODE_CBC` jest wartością domyślną, kod, którego to dotyczy, może nie mieć przypisanej żadnej wartości dla `BCRYPT_CHAINING_MODE`.

W przypadku programów utworzonych przy użyciu starszego interfejsu API usług kryptograficznych systemu Windows:

- Wywołanie odszyfrowujący jest [CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) z `Final=TRUE`.
- Obsługa klucza została zainicjowana przez wywołanie [CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam) z ustawionym na `CRYPT_MODE_CBC`[KP_MODE](/windows/desktop/api/wincrypt/nf-wincrypt-cryptgetkeyparam) .
  - Ponieważ `CRYPT_MODE_CBC` jest wartością domyślną, kod, którego to dotyczy, może nie mieć przypisanej żadnej wartości dla `KP_MODE`.

## <a name="finding-vulnerable-code---managed-applications"></a>Znajdowanie zagrożonych aplikacji zarządzanych przez kod

- Wywołanie odszyfrowywania to metody <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> lub <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> w <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.
  - Obejmuje to następujące typy pochodne w ramach platformy .NET, ale mogą również zawierać typy innych firm:
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
- Właściwość <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> została ustawiona na <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>lub <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.
  - Ponieważ <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> jest wartością domyślną, kod, którego to dotyczy, może nigdy nie mieć przypisanej właściwości <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType>.
- Właściwość <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> została ustawiona na <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType>
  - Ponieważ <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> jest wartością domyślną, kod, którego to dotyczy, może nigdy nie mieć przypisanej właściwości <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType>.

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a>Znajdowanie niezagrożonego kodu — składnia komunikatu kryptograficznego

Nieuwierzytelniony komunikat CMS EnvelopedData, którego zaszyfrowana zawartość używa trybu CBC AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) lub RC2 (1.2.840.113549.3.2) podatne na ataki, a także komunikaty używające innych algorytmów szyfrowania bloku w trybie CBC.

Chociaż szyfry strumienia nie są podatne na tę konkretną lukę w zabezpieczeniach, firma Microsoft zaleca zawsze uwierzytelnianie danych przez sprawdzenie wartości ContentEncryptionAlgorithm.

W przypadku zarządzanych aplikacji obiekt BLOB EnvelopedData CMS może zostać wykryty jako dowolna wartość, która jest przenoszona do <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.

W przypadku aplikacji natywnych można wykryć obiekt BLOB EnvelopedData CMS jako dowolną wartość dostarczoną do uchwytu CMS za pośrednictwem [CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) , którego [CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam) wynikiem jest `CMSG_ENVELOPED` i/lub dojście usługi CMS jest później wysyłane instrukcją `CMSG_CTRL_DECRYPT` za pośrednictwem [CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol).

## <a name="vulnerable-code-example---managed"></a>Przykład kodu zagrożonego

Ta metoda odczytuje plik cookie i odszyfrowuje go i nie jest widoczne sprawdzanie integralności danych. W związku z tym zawartość pliku cookie odczytywanego przez tę metodę może być zaatakowana przez użytkownika, który go otrzymał lub przez osobę atakującą, która uzyskała zaszyfrowaną wartość cookie.

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

## <a name="example-code-following-recommended-practices---managed"></a>Przykładowy kod zgodnie z zalecanymi praktykami — zarządzany

Następujący przykładowy kod używa niestandardowego formatu komunikatów

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

w przypadku, gdy identyfikatory algorytmów `cipher_algorithm_id` i `hmac_algorithm_id` są reprezentacją aplikacji lokalnych (niestandardowych) tych algorytmów. Identyfikatory te mogą mieć sens w innych częściach istniejącego protokołu obsługi komunikatów, a nie jako elementu ByteStream połączone.

Ten przykład używa również jednego klucza głównego, aby utworzyć zarówno klucz szyfrowania, jak i klucz HMAC. Jest to wygodne dla wygody do wyłączania aplikacji z pojedynczą aplikacją do aplikacji z podwójnym podwyższeniem poziomu i zapewnienia, że te dwa klucze są różne. Zapewnia to dalsze gwarancję, że klucz HMAC i klucz szyfrowania nie mogą zostać zsynchronizowane.

Ten przykład nie akceptuje <xref:System.IO.Stream> szyfrowania ani odszyfrowywania. Bieżący format danych sprawia, że szyfrowanie jednokrotne jest trudne, ponieważ wartość `hmac_tag` poprzedza tekst szyfrowany. Jednak ten format został wybrany, ponieważ zachowuje wszystkie elementy o stałym rozmiarze na początku, aby ułatwić dalsze zachowanie analizatora. Przy użyciu tego formatu danych możliwe jest odszyfrowanie jednokrotne, ale w celu zaimplementowania GetHashAndReset i sprawdzenia wyniku przed wywołaniem TransformFinalBlock należy zachować ostrożność. Jeśli szyfrowanie strumieniowe jest ważne, może być wymagany inny tryb AE.

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
