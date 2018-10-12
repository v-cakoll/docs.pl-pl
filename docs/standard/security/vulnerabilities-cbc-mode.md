---
title: Chronometraż luk, wraz z trybie CBC odszyfrowanie symetryczne, za pomocą wypełnienia
description: Dowiedz się, jak wykrywać i eliminowanie luk w zabezpieczeniach chronometrażu przy użyciu trybu odszyfrowanie symetryczne Cipher-Block Chaining (CBC), za pomocą wypełnienia.
ms.date: 06/12/2018
author: blowdart
ms.author: mairaw
ms.openlocfilehash: 4f1d6df3c0368fa0273d871ff32564c159e62a2c
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123647"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a>Chronometraż luk, wraz z trybie CBC odszyfrowanie symetryczne, za pomocą wypełnienia

Microsoft uważa, że nie jest już awaryjny do odszyfrowania danych zaszyfrowanych za pomocą trybu Cipher-Block Chaining (CBC) szyfrowania symetrycznego, gdy możliwe do zweryfikowania dopełnienie została zastosowana bez pierwszy zapewniania integralności szyfrowany, z wyjątkiem bardzo szczegółowych okoliczności. Tej oceny jest oparty na znane obecnie badań kryptograficznych. 

## <a name="introduction"></a>Wprowadzenie

Atak oracle dopełnienie to rodzaj ataku zaszyfrowanych danych, która umożliwia osobie atakującej na odszyfrowywanie zawartości danych, nie wiedząc o tym kluczu.

Oracle odnosi się do "Przekaż", które zapewnia osoby atakującej o akcji, które są one wykonywane jest prawidłowy lub nie. Wyobraź sobie odtwarzanie tablicy lub karty grę z elementem podrzędnym. Gdy twarzy świeci się za pomocą uśmiechu big Data, ponieważ Agnieszka jest ona o decyzji o dobrej, który jest oracle. Jako przeciwnik, umożliwia to oracle odpowiednio zaplanować przejście dalej.

Potrzebne jest dopełnienie konkretny termin kryptograficznych. Niektóre mechanizmów szyfrowania, które są algorytmy, używany do szyfrowania danych, pracować na bloki danych, w którym każdy blok ma stały rozmiar. Jeśli dane, które chcesz szyfrować nie wielkości do wypełnienia bloków, dane są dopełniane dopóki nie robi. Wiele form uzupełnienia wymagają tego uzupełnienia zawsze być obecne, nawet jeśli oryginalne dane wejściowe o wielkości. Dzięki temu uzupełnienia zawsze można bezpiecznie usunąć podczas odszyfrowywania.

Zestawiania dwie rzeczy, implementacji oprogramowania z firmą oracle dopełnienie, co spowoduje wyświetlenie czy odszyfrowane dane ma prawidłową dopełnienia. Coś, co jest proste i polega na zwrócenie wartości, która jest wyświetlany komunikat "Nieprawidłowe dopełnienie" lub coś bardziej skomplikowane, jak zdejmowanie znaczącym ulepszaniu warunków życia innym czasie do przetworzenia prawidłowe bloku, w przeciwieństwie do nieprawidłowy blok, może być programu oracle.

Szyfry opartej na blokach ma inną właściwość o nazwie trybu, który określa relację danych w pierwszym bloku z danymi w drugi blok, i tak dalej. Jest jednym z najczęściej używanych trybów CBC. CBC wprowadza początkowego bloku losowych, znane jako inicjowania wektora (IV) i łączy poprzedniego bloku z wynikiem statyczne szyfrowanie się to w taki sposób, że szyfrowania ten sam komunikat przy użyciu tego samego klucza nie zawsze generuje ten sam wynik w zaszyfrowanych.

Osoba atakująca może użyć wypełnienie bazy danych oracle, w połączeniu z struktury danych CBC, wysyłanie komunikatów nieco zmiany do kodu, który udostępnia programu oracle i nadal wysyłać danych do momentu programu oracle dowie się, dane są poprawne. Z tej odpowiedzi osoba atakująca może odszyfrować komunikatu bajt po bajcie.

Sieci nowoczesnych komputerowe są takie wysokiej jakości, że osoba atakująca może wykryć bardzo mały (mniej niż 0,1 ms) różnice w realizacji czasu w systemach zdalnych. Aplikacje, które są przy założeniu, że pomyślne odszyfrowywania tylko zdarzyć, gdy dane nie został naruszony, może być narażony na ataki z narzędzia, które są przeznaczone do zaobserwować różnice w odszyfrowywania zakończone powodzeniem i niepowodzeniem. Ta różnica czasu może być bardziej znaczące w niektórych językach i bibliotekach niż inne, teraz uważa się, to jest praktyczne przed zagrożeniami dla wszystkich języków i bibliotek w przypadku odpowiedzi awaria aplikacji jest brana pod uwagę.

Ten rodzaj ataku opiera się na możliwość zmieniania zaszyfrowanych danych i testowania wyników za pomocą programu oracle. Jedynym sposobem, aby w pełni zminimalizowania skuteczności ataku jest wykrywanie zmian w postaci zaszyfrowanych danych i odmawiają wykonywać w niej żadnych akcji. Standardowy sposób, w tym celu jest utworzenie sygnatury dla danych i zweryfikować ten podpis, zanim wszystkie operacje są wykonywane. Podpis musi być do sprawdzenia, nie można utworzyć przez osobę atakującą, w przeciwnym razie one może zmienić zaszyfrowane dane, a następnie obliczeń nowa sygnatura na podstawie zmienionych danych. Jeden typ wspólnego z odpowiednim podpisem jest znany jako kod uwierzytelniania wiadomości opartych na kluczach skrótu (metoda HMAC). HMAC różni się od sumy kontrolnej, w tym, że zajmuje klucza tajnego znanego tylko osoby produkujących HMAC i osoby, sprawdzanie poprawności go. Bez posiadania klucza nie można utworzyć poprawne HMAC. Po otrzymaniu dane będą zaszyfrowane dane, niezależnie obliczenia HMAC przy użyciu klucza tajnego, możesz i nadawcy udziału, a następnie porównaj HMAC one wysyłane przeciwko jednemu zostanie obliczona. To porównanie musi być stałą czasu, w przeciwnym razie po dodaniu innego oracle wykrywalny, pozwalając na inny rodzaj ataku.

Podsumowując używać dopełniana szyfrów blokowych CBC bezpiecznie, połączyć je z HMAC (lub innego sprawdzania integralności danych), który sprawdzania poprawności, porównanie stałym czasie przed podjęciem próby do odszyfrowania danych. Ponieważ wszystkie komunikaty zmienionego Poświęć chwilę kwota w tym samym, aby odpowiedź z informacją, nie będzie mógł ataku.

## <a name="who-is-vulnerable"></a>Kto jest zagrożone

Tę lukę w zabezpieczeniach dotyczy zarządzane i natywne aplikacje, które wykonują swoje własne szyfrowanie i odszyfrowywanie. Dane te obejmują na przykład:

- Aplikacja, która szyfruje pliku cookie do odszyfrowywania nowszej na serwerze.
- Aplikacja bazy danych, która umożliwia użytkownikom wstawić dane do tabeli, w których kolumny są później odszyfrować.
- Aplikacja transferu danych, która opiera się na szyfrowanie przy użyciu klucza wstępnego, aby chronić dane podczas przesyłania.
- Aplikacja, która szyfruje i odszyfrowuje wiadomości "od wewnątrz" tunelu TLS.

Należy pamiętać, że przy użyciu protokołu TLS samodzielnie może nie chronią w tych scenariuszach.

Narażone aplikacji:

- Odszyfrowuje dane przy użyciu trybu szyfrowania CBC z trybem weryfikowalny dopełnienie, takie jak ANSI X.923 lub PKCS #7.
- Wykonuje odszyfrowywania bez konieczności wykonywane sprawdzania integralności danych (za pośrednictwem komputera MAC lub asymetrycznego podpisu cyfrowego).

Dotyczy to również aplikacji utworzonych na szczycie abstrakcje w górnej części tych wartości pierwotnych, takie jak struktury EnvelopedData składnię wiadomości kryptograficznych (PKCS #7/CMS).

## <a name="related-areas-of-concern"></a>Pokrewne obszary zainteresowania

Badania doprowadziło firmy Microsoft, aby dodatkowo zajmującym wiadomości CBC, które są dopełniane ekwiwalent ISO 10126 wypełnienia podczas wiadomości ma strukturę stopki dobrze znanego lub przewidywalne. Na przykład zawartość przygotowany zgodnie z regułami składni szyfrowanie XML W3C i przetwarzanie zalecenie (xmlenc EncryptedXml). Gdy wskazówki W3C podpisywanie komunikatów, a następnie szyfrować została uznana za odpowiednie w czasie, firma Microsoft zaleca teraz zawsze podczas szyfrowania następnie logowania.

Deweloperzy aplikacji powinny zawsze być w trosce o sprawdzanie możliwości zastosowania klucza asymetrycznego podpis nie ma zaufania nieprzerwaną pracę relacji między klucza asymetrycznego i dowolnego komunikatu.

## <a name="details"></a>Szczegóły

W przeszłości było zgodne, które są ważne do szyfrowania i uwierzytelniania ważnych danych za pomocą środków, takich jak sygnatury HMAC lub RSA. Jednak nastąpiła mniej wyraźne wskazówki dotyczące sposobu sekwencji operacji szyfrowania i uwierzytelniania. Ze względu na usterkę szczegółowo opisane w tym artykule wskazówki dotyczące firmy Microsoft jest teraz zawsze używaj modelu "szyfrowania następnie logowania". Oznacza to najpierw szyfrowania danych przy użyciu klucza symetrycznego, a następnie obliczenia MAC lub podpis asymetrycznego za pośrednictwem szyfrowanego (zaszyfrowanych danych). Podczas deszyfrowania danych, należy przeprowadzić odwrotnej. Najpierw upewnij się, MAC lub podpis szyfrowany, a następnie go odszyfrować.

Klasa określane jako "dopełnienie oracle ataków" znane istniał ponad 10 lat luk w zabezpieczeniach. Te luki w zabezpieczeniach umożliwia atakującemu odszyfrować dane szyfrowane przez algorytmy symetryczne bloku, takie jak AES i 3DES, przy użyciu nie więcej niż 4096 prób na bloku danych. Wprowadź te luki w zabezpieczeniach użytkowania fakt, że block szyfry są najczęściej używane przy użyciu danych uzupełniania weryfikowalne na końcu. Ustalono, że jeśli osoba atakująca może manipulować tekstu szyfrowanego i Dowiedz się, czy naruszanie spowodował błąd w formacie uzupełnienia na końcu, osoba atakująca może odszyfrować danych.

Początkowo praktyczne ataków znajdowały się na usługami zwracającymi kody błędów różnych oparte na czy dopełnienie był prawidłowy, takich jak ASP.NET luk w zabezpieczeniach [MS10-070](/security-updates/SecurityBulletins/2010/ms10-070). Jednak program Microsoft teraz uważa, jest praktyczne przeprowadzenie podobne ataków przy użyciu tylko różnice czasu między przetwarzania dopełnienie prawidłowe i nieprawidłowe.

Pod warunkiem, że schemat szyfrowania wykorzystuje sygnatury i weryfikacji podpisu jest wykonywane przy użyciu stałej środowiska uruchomieniowego dla podanej długości data (niezależnie od zawartości), bez żadnych informacji do emitowania można zweryfikować integralności danych Osoba atakująca za pośrednictwem [kanału po stronie](https://en.wikipedia.org/wiki/Side-channel_attack). Ponieważ sprawdzania integralności odrzuca komunikaty zmodyfikowany, jest zmniejszany dopełnienie zagrożeń bazy danych oracle.

## <a name="guidance"></a>Wskazówki

Najpierw firma Microsoft zaleca, muszą być przekazywane za pośrednictwem zabezpieczeń TLS (Transport Layer), następca do Secure Sockets Layer (SSL) żadnych danych, który ma poufności.

Następnie analizowania aplikacji w taki sposób, aby:

- Dowiedz się dokładnie szyfrowania, jakie wykonujesz i jakie szyfrowanie jest świadczona przez platform i interfejsów API, używasz.
- Mieć pewność, że każdy użycia w każdej warstwie symetryczne [algorytmu szyfrowania bloku](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), takie jak AES i 3DES w trybie CBC zawierają użytkowania sprawdzania integralności danych opartych na kluczach klucz tajny (asymetrycznego sygnatury HMAC lub zmienić tryb szyfrowania do [uwierzytelnione szyfrowanie](https://en.wikipedia.org/wiki/Authenticated_encryption) trybu (AE), takich jak usługa GCM lub CCM).

Oparte na bieżących badaniach, ogólnie uważa się, że w przypadku uwierzytelniania i szyfrowania kroki są wykonywane niezależnie dla trybów AE bez szyfrowania, uwierzytelniania szyfrowanego (szyfrowanie następnie logowania) jest najlepszym rozwiązaniem ogólne. Jednak istnieje nie opracowanie poprawną odpowiedź na kryptografii i to uogólnienie nie jest tak dobre, jak ukierunkowanej porady z profesjonalnych cryptographer.

Aplikacje, które są nie można zmienić ich format wiadomości, ale wykonać nieuwierzytelnione CBC odszyfrowywania są zachęcani do próby takich jak zastosować środki zaradcze:

- Odszyfrowywanie, bez udzielania praw odszyfrowujący Sprawdź lub usunąć dopełnienie:
  - Wszelkie dopełnienie, które zostały zastosowane nadal musi zostać usunięta albo ignorowane, przenosisz obciążenia w aplikacji.
  - Korzyścią jest to, że wypełnienie weryfikacji i usuwania można zintegrować inną logikę weryfikacji danych aplikacji. Jeśli weryfikacja dopełnienie i weryfikacja danych może odbywać się w stałym czasie, zostanie zmniejszona zagrożenia.
  - Ponieważ interpretacji uzupełnienie Zmienia długość komunikatu postrzegany, może nadal być informacje o czasie emitowane przez to podejście.
- Zmień tryb uzupełniania odszyfrowywania ISO10126:
  - Dopełnienie odszyfrowywania ISO10126 jest zgodny z wypełnienie PKCS7 i wypełnienie ANSIX923.
  - Zmienianie trybu zmniejsza wiedzy oracle uzupełnienia do 1 bajt zamiast całego bloku. Jeśli zawartość ma dobrze znanych stopki, takich jak zamykającego elementu XML powiązane ataków jednak na ataki pozostałej części wiadomości.
  - To także nie uniemożliwia odzyskiwanie zwykłego tekstu w sytuacjach, w których osoba atakująca może przekształcić tego samego zwykłego tekstu do zaszyfrowania wiele razy z przesunięciem inny komunikat.
- Brama oceny Rozmoczenie sygnału czasu wywołania odszyfrowywania:
  - Obliczanie czasu wstrzymania musi mieć co najmniej przekraczające maksymalną ilość czasu, jaki zajęłoby operacji odszyfrowywania każdego segmentu danych, który zawiera dopełnienie.
  - Obliczeń czasu powinna być podejmowana zgodnie z zaleceniami w [uzyskiwania sygnatury czasowe o wysokiej rozdzielczości](https://msdn.microsoft.com/library/windows/desktop/dn55340.aspx), nie za pomocą <xref:System.Environment.TickCount?displayProperty=nameWithType> (zależnie od roll-over/przepełnienie) lub usunięcie dwóch system sygnatur czasowych (zależnie od korekty NTP błędy).
  - Obliczeń czasu musi być z uwzględnieniem operacji odszyfrowywania, w tym wszystkie potencjalne wyjątki w zarządzane lub aplikacji w języku C++, nie tylko o na końcu.
  - W przypadku powodzenia lub niepowodzenia ustalono jeszcze, brama chronometrażu musi zwracać błąd, po jego wygaśnięciu.
- Usługi, które wykonują nieuwierzytelnione odszyfrowywania powinny mieć monitorowania w miejscu, aby wykryć, czy powódź komunikatów "nieprawidłowy" stał się za pośrednictwem.
  - Mieć na uwadze, że ten sygnał niesie ze sobą wyniki fałszywie dodatnie (rzeczywiście uszkodzone dane) i fałszywych wyników negatywnych (rozkładanie ataku w czasie wystarczająco długi, w celu uniknięcia wykrycia).

## <a name="finding-vulnerable-code---native-applications"></a>Znajdowanie kodu luki w zabezpieczeniach — aplikacje natywne

Dla programów skompilowana kryptografii Windows: Biblioteka Next Generation (CNG):

- Wywołanie odszyfrowywania ma na celu [BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt), określanie `BCRYPT_BLOCK_PADDING` flagi.
- Uchwytu klucza został zainicjowany przez wywołanie metody [BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty) z [BCRYPT_CHAINING_MODE](https://msdn.microsoft.com/library/windows/desktop/aa376211.aspx#BCRYPT_CHAINING_MODE) równa `BCRYPT_CHAIN_MODE_CBC`.
  - Ponieważ `BCRYPT_CHAIN_MODE_CBC` jest zachowaniem domyślnym, wpływ na kod nie może mieć przypisany żadnej wartości dla `BCRYPT_CHAINING_MODE`.

Dla programów skompilowana starsze Cryptographic API Windows:

- Wywołanie odszyfrowywania ma na celu [CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) z `Final=TRUE`.
- Uchwytu klucza został zainicjowany przez wywołanie metody [CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam) z [KP_MODE](https://msdn.microsoft.com/library/windows/desktop/aa379949.aspx#KP_MODE) równa `CRYPT_MODE_CBC`.
  - Ponieważ `CRYPT_MODE_CBC` jest zachowaniem domyślnym, wpływ na kod nie może mieć przypisany żadnej wartości dla `KP_MODE`.

## <a name="finding-vulnerable-code---managed-applications"></a>Znajdowanie kodu luki w zabezpieczeniach — usługa managed applications

- Wywołanie odszyfrowywania ma na celu <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> lub <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> metod <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.
  - Zawiera następujące typy pochodne w ramach platformy .NET, ale mogą również zawierać typy innej firmy:
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
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> Właściwość <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>, lub <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.
  - Ponieważ <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> jest zachowaniem domyślnym, wpływ na kod nigdy nie może mieć przypisany <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> właściwości.
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> Właściwość <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType>
  - Ponieważ <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> jest zachowaniem domyślnym, wpływ na kod nigdy nie może mieć przypisany <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> właściwości.

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a>Znajdowanie kodu luki w zabezpieczeniach — składni wiadomości kryptograficznych

Nieuwierzytelnionych wiadomości CMS EnvelopedData, w których zaszyfrowaną zawartość korzysta z trybu CBC AES (2.16.840.1.101.3.4.1.2 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) lub RC2 (1.2.840.113549.3.2) jest narażony, jak również jako komunikatów w trybie CBC przy użyciu innych algorytmów szyfrowania bloku.

Gdy szyfrów strumienia nie są podatne na tę lukę w zabezpieczeniach w szczególności, firma Microsoft zaleca zawsze uwierzytelnianie dane za pośrednictwem sprawdzania wartości ContentEncryptionAlgorithm.

Dla zarządzanych aplikacji EnvelopedData CMS, obiekt blob może być wykryte wszelkie wartości, który jest przekazywany do <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.

Dla natywnych aplikacji można wykryć blob CMS EnvelopedData wartością dostarczane do uchwytu CMS za pośrednictwem [CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) którego wynikowa [CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam) jest `CMSG_ENVELOPED` i/lub uchwyt CMS później wysyłane `CMSG_CTRL_DECRYPT` instrukcji za pomocą [CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol).

## <a name="vulnerable-code-example---managed"></a>Przykład kodu luki w zabezpieczeniach — zarządzane

Ta metoda odczytuje plik cookie i odszyfrowuje je i sprawdzania integralności danych, nie jest widoczna. W związku z tym zawartość pliku cookie, który jest odczytywany przez tę metodę można zaatakowane przez użytkownika, który je lub przez każda osoba atakująca, która uzyskała wartość zaszyfrowanego pliku cookie.

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

## <a name="example-code-following-recommended-practices---managed"></a>Następujące kodu przykładzie zalecane praktyki — zarządzane

Następujący przykładowy kod używa formatu komunikatów niestandardowych

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

gdzie `cipher_algorithm_id` i `hmac_algorithm_id` algorytm identyfikatory są lokalnego aplikacji (niestandardowe) reprezentacje tych algorytmów. Tych identyfikatorów może mieć sens w innych częściach Twojego istniejącego protokołu obsługi komunikatów, zamiast jako bez połączonych elementu bytestream.

W tym przykładzie używa również jednego klucza głównego do wyprowadzenia zarówno klucz szyfrowania, jak i klucz HMAC. Jest to przewidziane zarówno jako udogodnienie włączenie aplikacji z kluczem pojedynczo do aplikacji opartych na kluczach procesory i zachęcenie utrzymywanie dwa klucze, jak różne wartości. Dodatkowo gwarantuje, nie można pobrać klucza HMAC i klucza szyfrowania tracą synchronizację.

W tym przykładzie nie zaakceptuje <xref:System.IO.Stream> do szyfrowania lub odszyfrowywania. Bieżące dane formatu sprawia, że jeden przebieg szyfrowania trudne ponieważ `hmac_tag` wartość poprzedza tekstu szyfrowanego. Jednak ten format wybrano, ponieważ zapewnia wszystkie elementy o stałym rozmiarze na początku zapewnienie analizator prostsze. Z tego formatu danych odszyfrowywania jeden przebieg jest możliwe, chociaż implementujący jest ostrzeżenie, aby wywołać GetHashAndReset i sprawdź wynik przed wywołaniem TransformFinalBlock. Jeśli szyfrowanie przesyłania strumieniowego jest ważne, inny tryb AE może być wymagane.

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
