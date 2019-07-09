---
title: Usługi kryptograficzne
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography [.NET Framework]
- pattern of derived class inheritance
- digital signatures
- asymmetric cryptographic algorithms
- digital signatures, public-key systems
- public keys
- decryption [.NET Framework]
- private keys
- MAC algorithms
- cryptographic algorithms
- private keys, overview
- encryption [.NET Framework]
- security [.NET Framework], encryption
- cryptographic services
- symmetric cryptographic algorithms
- hash
- message authentication codes
- derived class inheritance
- cryptography [.NET Framework], about
- random number generation
ms.assetid: f96284bc-7b73-44b5-ac59-fac613ad09f8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c026174e881768af245860d1b719184dc47f1798
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663988"
---
# <a name="cryptographic-services"></a>Usługi kryptograficzne

<a name="top"></a> Sieci publicznych, takich jak Internet nie zapewniają środek bezpiecznej komunikacji między jednostkami. Komunikacja za pośrednictwem tych sieci jest podatny na trwa odczytu lub nawet zmodyfikować nieautoryzowanym osobom trzecim. Kryptografia pomaga chronić dane przed wyświetlaniem, udostępnia metody wykrywania, czy dane zostały zmodyfikowane, a także pomaga w zapewnieniu bezpiecznego oznacza, że komunikacji za pośrednictwem kanałów w przeciwnym razie niezabezpieczone. Na przykład danych można być szyfrowane przy użyciu algorytmu kryptograficznego, przekazywane w stanu zaszyfrowanego i później odszyfrować zamierzony innych firm. Jeśli strona trzecia przechwytuje zaszyfrowane dane, będzie trudne do odszyfrowania.

W .NET Framework klas w <xref:System.Security.Cryptography?displayProperty=nameWithType> przestrzeni nazw Zarządzanie wiele szczegółów kryptografii. Niektóre są otoki dla niezarządzanych API kryptografii firmy Microsoft (CryptoAPI), a inne wyłącznie zarządzanej implementacji. Nie musisz być ekspertem w kryptografii do użycia w ramach tych zajęć. Podczas tworzenia nowego wystąpienia jednego z szyfrowania klasy algorytm klucze są automatycznie generowane w celu ułatwienia i domyślne właściwości są tak bezpieczne i bezpieczne, jak to możliwe.

W tym omówieniu przedstawiono streszczenie metod szyfrowanie i rozwiązań obsługiwanych przez program .NET Framework, w tym manifesty ClickOnce, Suite B i pomocy technicznej Cryptography Next Generation (CNG) wprowadzone w programie .NET Framework 3.5.

Ten przegląd zawiera następujące sekcje:

- [Podstawowych usług kryptograficznych](#primitives)

- [Klucz tajny szyfrowania](#secret_key)

- [Public-Key Encryption](#public_key)

- [Podpisy cyfrowe](#digital_signatures)

- [Wartości skrótów](#hash_values)

- [Generowanie liczby losowej](#random_numbers)

- [Manifesty ClickOnce](#clickonce)

- [Obsługa pakietu Suite B](#suite_b)

- [Tematy pokrewne](#related_topics)

Aby uzyskać dodatkowe informacje o kryptografii i usług firmy Microsoft, składniki i narzędzia, które pozwalają zwiększyć bezpieczeństwo kryptograficzne dla poszczególnych aplikacji Zobacz Win32 i COM, rozwoju, sekcji Zabezpieczenia w niniejszej dokumentacji.

<a name="primitives"></a>

## <a name="cryptographic-primitives"></a>Podstawowych usług kryptograficznych

W typowej sytuacji kryptografii jest używane w sytuacji obie strony (Alice i Bob) komunikują się za pośrednictwem niezabezpieczonych kanału. Alice i Bob chcesz zapewnić niezrozumiała każdy, kto może nasłuchiwać komunikacji. Ponadto ponieważ Alice i Bob znajdują się w lokalizacjach zdalnych, Alicja musisz upewnić się, że informacje, które otrzyma ona z Bob nie został zmodyfikowany przez dowolną osobę podczas transmisji. Ponadto ona musisz upewnić się, że informacje naprawdę pochodzą z niego, a nie z osobą, która personifikuje Bob.

Kryptografia jest wykorzystywana do osiągnięcia następujących celów:

- Poufność: Aby pomóc w ochronie tożsamości użytkownika lub danych z odczytu.

- Integralność danych: Aby chronić dane przed zmianami.

- Uwierzytelnianie: Aby upewnić się, że dane pochodzą z określoną stroną.

- Niemożność wyparcia się: Aby zapobiec konkretnej strony odmowy wysłał wiadomość.

Aby osiągnąć te cele, umożliwia kombinacji algorytmów i praktyk, znane jako podstawowych usług kryptograficznych tworzenie schematu kryptograficznego. W poniższej tabeli wymieniono prymitywów kryptograficznych i ich zastosowań.

|Pierwotny kryptograficzne|Zastosowanie|
|-----------------------------|---------|
|Klucz tajny szyfrowania (Kryptografia symetryczna)|Wykonuje przekształcenie danych, aby zapobiec odczytywany przez osoby trzecie. Ten typ szyfrowania używa pojedyncza, współdzielona, klucza tajnego szyfrowania i odszyfrowywania danych.|
|Szyfrowanie klucza publicznego (kryptografii asymetryczny)|Wykonuje przekształcenie danych, aby zapobiec odczytywany przez osoby trzecie. Ten typ szyfrowania do szyfrowania i odszyfrowywania danych korzysta z pary kluczy publiczny/prywatny.|
|Podpisywanie kryptograficzne|Pomaga sprawdzić pochodzą dane z określonej innej firmy, tworząc podpis cyfrowy, który jest unikatowy dla tej strony. Ten proces jest również używa funkcji mieszania.|
|Skróty kryptograficzne|Mapuje dane z dowolnej długości sekwencji bajtów o stałej długości. Skróty są statystycznie unikatowy. inną kombinację dwóch bajtów nie będzie skrótu na tę samą wartość.|

[Powrót do początku](#top)

<a name="secret_key"></a>

## <a name="secret-key-encryption"></a>Klucz tajny szyfrowania

Algorytmy szyfrowania klucz tajny użyć pojedynczego klucza tajnego do szyfrowania i odszyfrowywania danych. Należy zabezpieczyć klucza przed dostępem nieautoryzowanych agentów, ponieważ każda strona, która ma klucz służy do odszyfrowywania danych lub szyfrować dane, zgłaszanie się, że pochodzi ze strony użytkownika.

Klucz tajny szyfrowania jest również określany jako szyfrowania symetrycznego, ponieważ ten sam klucz służy do szyfrowania i odszyfrowywania. Algorytmy szyfrowania klucz tajny są bardzo szybko (w porównaniu z algorytmami klucz publiczny) i dobrze nadaje się do wykonywania przekształceniami kryptograficznymi dużych strumieni danych. Szyfrowanie asymetryczne algorytmy, takie jak RSA są ograniczone ze sobą matematycznie w ilości danych można zaszyfrować. Algorytmy szyfrowania symetrycznego nie mają zazwyczaj tych problemów.

Typ algorytmu klucz tajny o nazwie szyfrowania bloku jest używany do szyfrowania jeden blok danych w danym momencie. Blok szyfrów, takie jak Data Encryption Standard (DES), TripleDES, i Advanced Encryption Standard (AES) kryptograficznie przekształcania danych wejściowych blok *n* bajtów do bloku danych wyjściowych zaszyfrowanych bajtów. Jeśli chcesz zaszyfrować lub odszyfrować sekwencji bajtów, trzeba go blok po bloku. Ponieważ *n* jest mały (8 bajtów DES i TripleDES; 16-bajtowy [domyślnie], w bajtach 24 lub 32 bajty w przypadku standardu AES), wartości danych, które są większe niż *n* muszą być szyfrowane jednego bloku naraz. Wartości danych, które są mniejsze niż *n* trzeba można rozszerzyć, aby *n* w celu przetworzenia.

Jeden prosty formularz szyfrem nosi nazwę trybu codebook elektronicznej (ECB). Tryb ECB jest uważana za niebezpieczną, ponieważ nie jest używane wektor inicjowania do inicjowania pierwszego bloku w postaci zwykłego tekstu. Dla danego klucza tajnego *k*, cipher Prosty blok, który nie korzysta z wektor inicjowania spowoduje zaszyfrowanie tego samego bloku danych wejściowych zwykłego tekstu do tego samego bloku danych wyjściowych tekstu szyfrowanego. W związku z tym jeśli masz zduplikowanych bloków w strumienia danych wejściowych w postaci zwykłego tekstu, konieczne będzie zduplikowanych bloków w danych wyjściowych strumienia tekstu szyfrowanego. Te bloki zduplikowany wyjściowy alertu nieautoryzowanym użytkownikom słabe szyfrowanie używane algorytmy, które może być zatrudnionych i możliwe tryby ataku. Trybu szyfrowania ECB występuje w związku z tym dość analizy i ostatecznie kluczy odnajdywania.

Klasy szyfrowania bloku, które znajdują się w bibliotece klasy bazowej użyć domyślnego łańcucha tryb o nazwie szyfrowania bloku łańcucha (CBC), mimo że można zmienić to ustawienie domyślne, jeśli chcesz.

Szyfry CBC rozwiązywania problemów związanych z mechanizmów szyfrowania ECB przy użyciu wektor inicjowania (IV) do zaszyfrowania pierwszego bloku zwykłego tekstu. Każdy blok kolejnych zwykłego tekstu ulega bitowe wykluczające OR (`XOR`) operację, używając poprzedniego bloku szyfrowany przed jest zaszyfrowany. Każdy blok tekstu szyfrowanego w związku z tym jest zależna od wszystkich poprzednich blokach. Gdy ten system jest nagłówków wiadomości używane, wspólnego, które mogą być znane nieautoryzowanym użytkownikom nie może być używany do odtwarzanie klucza.

Jednym ze sposobów naruszyć bezpieczeństwo danych, które są szyfrowane za pomocą szyfrowania CBC jest przeprowadzenie kompleksowe przeszukiwanie co możliwe klucza. W zależności od rozmiaru klucza, który jest używany do szyfrowania tego rodzaju wyszukiwania jest bardzo czasochłonne, za pomocą nawet komputerów najszybszy i dlatego niewykonalne. Większe rozmiary kluczy są trudniejsze do odszyfrowania. Mimo że szyfrowania nie uniemożliwiają teoretycznie dla osoby atakującej pobierania zaszyfrowanych danych, jej podnieść koszt w ten sposób. Jeśli zajmuje trzy miesiące, aby wykonać kompleksowe przeszukiwanie do pobierania danych, która ma znaczenie tylko przez kilka dni, metoda kompleksowe przeszukiwanie jest niepraktyczne.

Wadą szyfrowania klucz tajny jest zakłada obie strony mają uzgodniono klucza i IV i przekazywane ich wartości. IV nie jest uważany za wpisu tajnego i mogą być przesyłane w postaci zwykłego tekstu z komunikatem. Jednak klucz muszą być trzymane w tajemnicy przed nieautoryzowanymi użytkownikami. Z powodu problemów z tymi szyfrowania klucz tajny jest często używana razem z szyfrowania klucza publicznego do prywatnie komunikacji wartości klucza i IV.

Przy założeniu, że Alice i Bob znajdują się dwie strony, które mają do komunikacji za pośrednictwem niezabezpieczonych kanału, mogą użyć szyfrowania klucz tajny w następujący sposób: Alice i Bob zobowiązuje się do jednego określonego algorytmu (na przykład AES) za pomocą określonego klucza i IV. Alicja Redaguj komunikat i tworzy strumień sieci (być może nazwanego potoku lub sieci poczty e-mail), na którym chcesz wysłać wiadomość. Następnie użytkownik szyfruje tekst przy użyciu klucza i IV i wysyła zaszyfrowanego komunikatu i IV do niego za pośrednictwem sieci intranet. Robert otrzymuje zaszyfrowanego tekstu i odszyfrowuje ją przy użyciu IV i wcześniej uzgodnionych klucza. W przypadku przechwycenia transmisji interceptor nie można odzyskać oryginalnej wiadomości, ponieważ nie zna klucza. W tym scenariuszu tylko klucz musi pozostać wpisu tajnego. W rzeczywistym scenariuszu Alice i Bob generuje klucz tajny i przenieść klucz tajny (symetrycznego) do drugiej strony jest używane szyfrowanie (asymetrycznie) klucz publiczny. Aby uzyskać więcej informacji o szyfrowaniu klucza publicznego zobacz następną sekcję.

Program .NET Framework zawiera następujące klasy, które implementują algorytmy szyfrowania klucz tajny:

- <xref:System.Security.Cryptography.AesManaged> (wprowadzona w programie .NET Framework 3.5).

- <xref:System.Security.Cryptography.DESCryptoServiceProvider>.

- <xref:System.Security.Cryptography.HMACSHA1> (Jest to technicznie algorytm klucz tajny, ponieważ reprezentuje on kod uwierzytelniania wiadomości, która jest obliczana przy użyciu funkcji skrótu kryptograficznego w połączeniu z klucz tajny. Zobacz [wartości skrótu](#hash_values)w dalszej części tego tematu.)

- <xref:System.Security.Cryptography.RC2CryptoServiceProvider>.

- <xref:System.Security.Cryptography.RijndaelManaged>.

- <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>.

[Powrót do początku](#top)

<a name="public_key"></a>

## <a name="public-key-encryption"></a>Public-Key Encryption

Szyfrowanie klucza publicznego używa klucza prywatnego, które muszą być trzymane w tajemnicy przed nieautoryzowanymi użytkownikami i kluczem publicznym, które mogą być ujawniane nikomu. Klucz publiczny i klucz prywatny są ze sobą matematycznie powiązane; można odszyfrować danych, które są szyfrowane przy użyciu klucza publicznego tylko przy użyciu klucza prywatnego i danych, który jest podpisany przy użyciu klucza prywatnego, można sprawdzić tylko przy użyciu klucza publicznego. Klucz publiczny mogą być udostępniane osobom; Służy do szyfrowania danych do wysłania do hodowca klucza prywatnego. Algorytmy kryptograficzne klucza publicznego są również nazywane asymetryczne algorytmy, ponieważ jeden klucz jest wymagany do szyfrowania danych, a inny klucz jest wymagany do odszyfrowania danych. Podstawową regułę kryptograficznych uniemożliwia ponowne użycie klucza, a oba klucze, powinien być unikatowy dla każdej sesji komunikacji. Jednak w praktyce ogólnie długotrwałe są klucze asymetryczne.

Obie strony (Alice i Bob) może używać szyfrowania klucza publicznego w następujący sposób: Po pierwsze Alicja generowana jest para kluczy publiczny/prywatny. Jeśli Bob chce, aby wysłać wiadomość zaszyfrowaną Alicja, zwróci się więc do jej dla swojego klucza publicznego. Alicja wysyła Bob jej klucz publiczny za pośrednictwem niezabezpieczonej sieci, a Bob używa tego klucza szyfrowania wiadomości. Robert wysyła zaszyfrowanego komunikatu do Alicji, a ona odszyfrowuje je, używając swojego klucza prywatnego. Jeśli Bob odebrane przez Alice klucz za pośrednictwem niezabezpieczonych kanału, takich jak sieć publiczną Bob jest otwarty na atak typu man-in--middle. W związku z tym Bob należy sprawdzić za pomocą Alicja, że ma on poprawny kopię jej klucz publiczny.

Podczas przekazywania klucza publicznego Alicji nieautoryzowany agent może przechwycić klucza. Ponadto ten sam agent może przechwycić zaszyfrowanego komunikatu z niego. Jednak agent nie może odszyfrować wiadomości przy użyciu klucza publicznego. Komunikat mogły być odszyfrowane tylko przy użyciu klucza prywatnego przez Alice, które nie zostały przekazane. Alicja nie używa swojego klucza prywatnego do zaszyfrowania komunikatu odpowiedzi do Boba, ponieważ każda osoba z kluczem publicznym można odszyfrować wiadomości. Jeśli Alicja chce, aby wysłać wiadomość do Roberta, ona zadaje Bob dla swojego klucza publicznego, a następnie szyfruje jej wiadomości przy użyciu tego klucza publicznego. Bob odszyfrowuje wiadomości za pomocą jego skojarzonego klucza prywatnego.

W tym scenariuszu Alice i Bob szyfrowania klucza publicznego (asymetrycznie) do przekazania klucza tajnego klucza (symetrycznego) i klucz tajny szyfrowania w pozostałej części sesji.

Poniższa lista zawiera porównanie klucz publiczny i klucz tajny algorytmów kryptograficznych:

- Algorytmy kryptograficzne klucza publicznego używany rozmiar ustalony bufor, klucz tajny algorytmy kryptograficzne używane bufor o zmiennej długości.

- Algorytmy kluczy publicznych nie można użyć do łańcucha danych razem do strumieni sposób, w jaki można algorytmy klucz tajny, ponieważ tylko niewielkich ilości danych, które mogą być szyfrowane. W związku z tym asymetryczne operacje nie należy używać tego samego modelu przesyłania strumieniowego jako operacje symetryczne.

- Szyfrowanie klucza publicznego ma znacznie większych przestrzeń kluczy (zakres możliwych wartości dla klucza) niż klucz tajny szyfrowania. Dlatego szyfrowanie klucza publicznego jest mniej podatny na ataki wyczerpująca, próbujących za każdy klucz możliwe.

- Klucze publiczne są łatwe do dystrybucji, ponieważ nie mają zostać zabezpieczone, pod warunkiem, że istnieje jakiś sposób, aby zweryfikować tożsamość nadawcy.

- Niektóre algorytmy klucza publicznego (np. RSA i DSA, ale nie Diffie-Hellman) może służyć do tworzenia podpisów cyfrowych, aby sprawdzić tożsamość nadawcy danych.

- Algorytmy klucza publicznego są bardzo wolne w porównaniu z algorytmami klucz tajny, a nie są przeznaczone do zaszyfrowania dużych ilości danych. Algorytmy klucza publicznego są przydatne tylko w przypadku przesyłania bardzo małe ilości danych. Zazwyczaj szyfrowania klucza publicznego jest używany do szyfrowania klucza i IV, który będzie używany przez algorytm klucz tajny. Po przesłaniu klucza i IV szyfrowania klucz tajny jest używana w pozostałej części sesji.

Program .NET Framework zawiera następujące klasy, które implementują algorytmy szyfrowania klucza publicznego:

- <xref:System.Security.Cryptography.DSACryptoServiceProvider>

- <xref:System.Security.Cryptography.RSACryptoServiceProvider>

- <xref:System.Security.Cryptography.ECDiffieHellman> (klasa podstawowa)

- <xref:System.Security.Cryptography.ECDiffieHellmanCng>

- <xref:System.Security.Cryptography.ECDiffieHellmanCngPublicKey> (klasa podstawowa)

- <xref:System.Security.Cryptography.ECDiffieHellmanKeyDerivationFunction> (klasa podstawowa)

- <xref:System.Security.Cryptography.ECDsaCng>

RSA umożliwia szyfrowania i podpisywania, ale DSA może służyć tylko do podpisywania, a Diffie'ego-Hellmana mogą służyć tylko do generowania kluczy. Ogólnie rzecz biorąc algorytmów klucza publicznego są bardziej ograniczone ich zastosowań niż algorytmów klucza prywatnego.

[Powrót do początku](#top)

<a name="digital_signatures"></a>

## <a name="digital-signatures"></a>Podpisy cyfrowe

Algorytmy kluczy publicznych może służyć również do tworzenia podpisów cyfrowych. Podpisy cyfrowe uwierzytelnianie tożsamości nadawcy (Jeśli ufasz nadawcy klucz publiczny) oraz pomóc je zabezpieczyć integralności danych. Za pomocą klucza publicznego, generowane przez Alice, Odbiorca danych Alicji można sprawdzić, że Alicja wysyłane go przez porównanie podpis cyfrowy do Alicji danych i klucza publicznego Alicji.

Aby używać kryptografii klucza publicznego do cyfrowego podpisywania wiadomości, Alicja najpierw dotyczy algorytmu wyznaczania wartości skrótu wiadomości, aby utworzyć skrót wiadomości. Skrót wiadomości jest zwarty i unikatowy reprezentacja danych. Alicja następnie szyfruje skrót wiadomości przy użyciu swojego klucza prywatnego do utworzenia jej podpisu. Po odebraniu wiadomości i podpisie, Robert odszyfrowuje podpisu przy użyciu klucza publicznego Alicji do odzyskania skrót wiadomości i skróty wiadomości za pomocą tego samego algorytmu wyznaczania wartości skrótu, używanym przez Alice. Skrót wiadomości, że Bob oblicza dokładnie odpowiada skrót wiadomości otrzymanych od Alicji, Roberta ma pewność, że wiadomość pochodzi z inicjator klucz prywatny oraz czy dane nie zostały zmodyfikowane. Bob zaufania, że Alicja jest inicjator klucza prywatnego, zna się, że wiadomość pochodzi od Alicji.

> [!NOTE]
> Podpis można sprawdzić przez nikogo, ponieważ klucz publiczny nadawcy jest popularną wiedzę i najczęściej przygotowywanych do uwzględnienia w formacie podpisu cyfrowego. Ta metoda nie zachowuje poufność wiadomości; wiadomości tajne go musi również być szyfrowana.

Program .NET Framework zawiera następujące klasy, które implementują algorytmy podpis cyfrowy:

- <xref:System.Security.Cryptography.DSACryptoServiceProvider>

- <xref:System.Security.Cryptography.RSACryptoServiceProvider>

- <xref:System.Security.Cryptography.ECDsa> (klasa podstawowa)

- <xref:System.Security.Cryptography.ECDsaCng>

 [Powrót do początku](#top)

<a name="hash_values"></a>

## <a name="hash-values"></a>Wartości skrótów

Algorytmy wyznaczania wartości skrótu wartości binarnych o dowolnej długości są mapowane na mniejsze wartości binarnych o stałej długości, znane jako wartości skrótu. Wartość skrótu jest numeryczna reprezentacja elementu danych. Wyznaczania wartości skrótu akapitu zwykłego tekstu i zmień nawet jednej litery akapitu, kolejne wyznaczania wartości skrótu powoduje wygenerowanie inną wartość. Jeśli wartość skrótu jest kryptograficznie silnej, jego wartość znacznie się zmieni. Na przykład jeśli pojedynczy bit wiadomości zostanie zmieniony, funkcję silne mieszania może powodować danych wyjściowych, który różni się o 50%. Wiele wartości wejściowe mogą skrótu na tę samą wartość w danych wyjściowych. Jednak go jest praktycznie niemożliwe Znajdź skrót do tej samej wartości dwóch różnych danych wejściowych.

Obie strony (Alice i Bob) można używać funkcji skrótu do zapewnienia integralności komunikatu. Użytkownik może wybrać algorytm wyznaczania wartości skrótu, aby zarejestrować swoje wiadomości. Alicja będzie zapisać komunikat, a następnie utwórz skrót tego komunikatu przy użyciu wybranego algorytmu. One będą następnie wykonaj jedną z następujących metod:

- Alicja wysyła wiadomości w postaci zwykłego tekstu i skrótu wiadomości (podpis cyfrowy) do niego. Robert otrzymuje wyznacza wartość skrótu wiadomości i porównuje jego wartość skrótu, aby wartość skrótu, który on otrzymany od Alice. Jeśli wartości skrótu są identyczne, wiadomość nie została zmieniona. Jeśli wartości nie są identyczne, komunikat zostało zmienione po jego autorem, Alicji.

  Niestety ta metoda nie można ustalić autentyczności nadawcy. Każdy może spersonifikować Alicja i wysłać wiadomość do niego. Używają tego samego algorytmu wyznaczania wartości skrótu do podpisania wiadomości, a wszystko, co można określić Bob to, czy komunikat odpowiada jego podpisu. Jest to jeden formularz atak typu man-in--middle. Aby uzyskać więcej informacji, zobacz [przykład komunikacji Secure Cryptography Next Generation (CNG)](https://docs.microsoft.com/previous-versions/cc488018(v=vs.100)).

- Alicja wysyła wiadomości w postaci zwykłego tekstu do niego za pośrednictwem niezabezpieczonych kanału publicznych. Wysyła skrótu wiadomości do niego za pośrednictwem bezpiecznego kanału prywatnych. Robert otrzymuje komunikat w postaci zwykłego tekstu, skróty go i porównuje skrót do prywatnie wymiana skrótu. Jeśli skróty są zgodne, Robert wie, dwie rzeczy:

  - Wiadomość nie została zmodyfikowana.

  - Nadawca wiadomości (Alice) jest autentyczny.

  Dla tego systemu do pracy Alicja należy ukryć swojej oryginalnej wartości skrótu od wszystkich stron z wyjątkiem sytuacji Bob.

- Alicja wysyła wiadomości w postaci zwykłego tekstu do niego za pośrednictwem niezabezpieczonych kanału publicznych i umieszcza skrótu wiadomości w publicznie dostępnej witrynę sieci Web.

  Ta metoda zapobiega, komunikat o naruszeniu, uniemożliwiając każdy przy użyciu wartości skrótu. Mimo, że komunikat i jego skrót mogą być odczytywane przez nikogo, można zmienić tylko przez Alice wartość skrótu. Osoba atakująca, która chce, aby dokonać personifikacji Alicja będzie wymagać dostępu do witryny sieci Web Alicji.

Żaden z poprzednich metod uniemożliwi ktoś odczytywania komunikatów przez Alice, ponieważ są one przekazywane w postaci zwykłego tekstu. Pełne zabezpieczenia zwykle wymaga (podpisywanie komunikatów) podpisów cyfrowych i szyfrowania.

Program .NET Framework zawiera następujące klasy, które implementują algorytmy wyznaczania wartości skrótu:

- <xref:System.Security.Cryptography.HMACSHA1>.

- <xref:System.Security.Cryptography.MACTripleDES>.

- <xref:System.Security.Cryptography.MD5CryptoServiceProvider>.

- <xref:System.Security.Cryptography.RIPEMD160>.

- <xref:System.Security.Cryptography.SHA1Managed>.

- <xref:System.Security.Cryptography.SHA256Managed>.

- <xref:System.Security.Cryptography.SHA384Managed>.

- <xref:System.Security.Cryptography.SHA512Managed>.

- Warianty HMAC wszystkich algorytmów Secure Hash Algorithm (SHA), Message Digest 5 (MD5) i RIPEMD 160.

- Implementacje CryptoServiceProvider (kod zarządzany otok) algorytmów SHA.

- Cryptography Next Generation (CNG) implementacji wszystkich algorytmów MD5 i SHA.

> [!NOTE]
> Wady projektowe MD5 zostały odnalezione w 1996 roku i SHA-1 został zalecony, zamiast tego. W 2004 r. dodatkowe wady zostały odnalezione, a algorytm MD5 przestaje być uważany za bezpieczny. Również wykryto algorytm SHA-1 jako niebezpieczne i SHA-2 jest teraz zalecane zamiast tego.

[Powrót do początku](#top)

<a name="random_numbers"></a>

## <a name="random-number-generation"></a>Generowanie liczby losowej

Generowanie liczby losowej jest integralną częścią wielu operacji kryptograficznych. Na przykład klucze kryptograficzne muszą być jako losowych, jak to możliwe, aby była możliwość ich odtworzenia. Kryptograficznych generatorów liczb losowych, należy wygenerować dane wyjściowe, który jest praktycznie niemożliwe do prognozowania z prawdopodobieństwem, który jest lepsze niż połowy. W związku z tym każda metoda przewidywania dalej bitu danych wyjściowych nie musi wykonywać lepiej niż zgadywania losowych. Klasy w .NET Framework Użyj generatorów liczb losowych do wygenerowania kluczy kryptograficznych.

<xref:System.Security.Cryptography.RNGCryptoServiceProvider> Klasa jest implementacją algorytm generator liczb losowych.

[Powrót do początku](#top)

<a name="clickonce"></a>

## <a name="clickonce-manifests"></a>Manifesty ClickOnce

W .NET Framework 3.5 następujące klasy kryptografii umożliwiają uzyskanie i sprawdź informacje dotyczące manifestu podpisów dla aplikacji, które są wdrażane przy użyciu [technologii ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment):

- <xref:System.Security.Cryptography.ManifestSignatureInformation> Klasy uzyskuje informacje o podpisie manifestu, korzystając z jego <xref:System.Security.Cryptography.ManifestSignatureInformation.VerifySignature%2A> przeciążenia metody.

- Możesz użyć <xref:System.Security.ManifestKinds> wyliczeniu, aby określić, które manifesty, aby sprawdzić. Wynik weryfikacji jest jednym z <xref:System.Security.Cryptography.SignatureVerificationResult> wartości wyliczenia.

- <xref:System.Security.Cryptography.ManifestSignatureInformationCollection> Klasy zawiera tylko do odczytu zbiór <xref:System.Security.Cryptography.ManifestSignatureInformation> obiektów zweryfikowanych podpisów.

 Ponadto następujące klasy zawierają informacje o określonej sygnaturze:

- <xref:System.Security.Cryptography.StrongNameSignatureInformation> Przechowuje informacje podpisu silnej nazwy dla manifestu.

- <xref:System.Security.Cryptography.X509Certificates.AuthenticodeSignatureInformation> przedstawia informacje o podpisie Authenticode dla manifestu.

- <xref:System.Security.Cryptography.X509Certificates.TimestampInformation> zawiera informacje o sygnaturę czasową na podpis Authenticode.

- <xref:System.Security.Cryptography.X509Certificates.TrustStatus> zapewnia prosty sposób, aby sprawdzić, czy podpis Authenticode jest zaufany.

[Powrót do początku](#top)

<a name="suite_b"></a>

## <a name="suite-b-support"></a>Obsługa pakietu Suite B

.NET Framework 3.5 obsługuje zestaw Suite B algorytmów kryptograficznych opublikowane przez National Security Agency (NSA). Aby uzyskać więcej informacji na temat pakietu Suite B, zobacz [NSA pakiet B kryptografii zestawieniem](https://www.nsa.gov/what-we-do/information-assurance/).

Uwzględnione są następujące algorytmy:

- Advanced Encryption Standard (AES) algorytmu klucza rozmiarach 128, 192 i 256 bitów na potrzeby szyfrowania.

- Bezpieczne algorytmy wyznaczania wartości skrótu SHA-1, SHA-256, SHA-384 i SHA-512, tworzenia skrótu (Ostatnie trzy ogólnie zgrupowanych razem i nazywany SHA-2.)

- Elliptic krzywej cyfrowego Signature Algorithm (ECDSA), za pomocą krzywych 256-bitowego, 384-bitowy i 521-bitowy moduli prime do podpisywania. Dokumentacja NSA specjalnie definiuje te krzywe i je wywołuje p-256, p-384 i p-521. Ten algorytm jest świadczona przez <xref:System.Security.Cryptography.ECDsaCng> klasy. Pozwala ona zalogowania się przy użyciu klucza prywatnego i zweryfikować podpisu przy użyciu klucza publicznego.

- Elliptic algorytmu Diffie-Hellman krzywej (ECDH), przy użyciu krzywych 256-bitowego, 384-bitowy i 521-bitowy moduli prime wymiany klucza i wpisu tajnego umowy. Ten algorytm jest świadczona przez <xref:System.Security.Cryptography.ECDiffieHellmanCng> klasy.

Kod zarządzany otok dla informacji o przetwarzaniu Standard FIPS (Federal) certyfikowane implementacje AES, SHA-256, SHA-384 i SHA-512 implementacje są dostępne w nowym <xref:System.Security.Cryptography.AesCryptoServiceProvider>, <xref:System.Security.Cryptography.SHA256CryptoServiceProvider>, <xref:System.Security.Cryptography.SHA384CryptoServiceProvider>, i <xref:System.Security.Cryptography.SHA512CryptoServiceProvider> klasy.

[Powrót do początku](#top)

<a name="cng"></a>

## <a name="cryptography-next-generation-cng-classes"></a>Kryptografia następnej generacji (CNG) klasy

Klasy Cryptography Next Generation (CNG) zapewniają zarządzanych otokę funkcji natywnych CNG. (CNG jest zamiennikiem CryptoAPI). Te klasy mają "Cng" w ramach ich nazw. Centralnej do klas otoki CNG jest <xref:System.Security.Cryptography.CngKey> klucza klasy kontenera, która przenosi magazyn i korzystanie z kluczami CNG. Ta klasa pozwala bezpiecznie przechowywać pary kluczy lub klucz publiczny i odwoływać się do niego za pomocą nazwy ciągu proste. Eliptyczne opartej na krzywej <xref:System.Security.Cryptography.ECDsaCng> Klasa podpisu i <xref:System.Security.Cryptography.ECDiffieHellmanCng> klasy szyfrowania można używać <xref:System.Security.Cryptography.CngKey> obiektów.

<xref:System.Security.Cryptography.CngKey> Klasa jest używana dla różnych dodatkowe operacje, w tym otwierania, tworzenie i eksportowanie kluczy. Umożliwia także dostęp do podstawowego dojścia klucza do użycia podczas wywoływania funkcji natywnych bezpośrednio.

.NET Framework 3.5 zawiera także szereg Obsługa klasy CNG, takie jak następujące:

- <xref:System.Security.Cryptography.CngProvider> przechowuje dostawca magazynu kluczy.

- <xref:System.Security.Cryptography.CngAlgorithm> obsługuje algorytm CNG.

- <xref:System.Security.Cryptography.CngProperty> utrzymuje często używanych właściwości klucza.

[Powrót do początku](#top)

<a name="related_topics"></a>

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Model kryptografii](../../../docs/standard/security/cryptography-model.md)|W tym artykule opisano, jak kryptografii jest zaimplementowane w bibliotece klas podstawowych.|
|[Przewodnik: Tworzenie aplikacji kryptograficznej](../../../docs/standard/security/walkthrough-creating-a-cryptographic-application.md)|Pokazuje podstawowe zadania szyfrowania i odszyfrowywania.|
|[Konfigurowanie klas kryptografii](../../../docs/framework/configure-apps/configure-cryptography-classes.md)|W tym artykule opisano sposób mapowania nazwy algorytmu kryptograficznego klasy i mapowanie identyfikatorów obiektów na algorytm kryptograficzny.|
