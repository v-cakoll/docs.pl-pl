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
ms.openlocfilehash: c1783a578d0b55b0b62a1ffb870802faca97623f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187009"
---
# <a name="cryptographic-services"></a>Usługi kryptograficzne

Sieci publiczne, takie jak Internet, nie zapewniają środków bezpiecznej komunikacji między podmiotami. Komunikacja za pomocą takich sieci jest podatna na odczyt, a nawet modyfikację przez nieupoważnione osoby trzecie. Kryptografia pomaga chronić dane przed ich przeglądaniem, zapewnia sposoby wykrywania, czy dane zostały zmodyfikowane, i pomaga zapewnić bezpieczne środki komunikacji za pośrednictwem kanałów niezabezpieczonych. Na przykład dane mogą być szyfrowane przy użyciu algorytmu kryptograficznego, przesyłane w stanie zaszyfrowanym, a następnie odszyfrowywane przez planowaną stronę. Jeśli osoba trzecia przechwyci zaszyfrowane dane, będzie to trudne do odszyfrowania.

W .NET Framework klasy w <xref:System.Security.Cryptography?displayProperty=nameWithType> przestrzeni nazw zarządzać wiele szczegółów kryptografii dla Ciebie. Niektóre z nich są otoki dla niezarządzanego interfejsu API kryptografii firmy Microsoft (CryptoAPI), podczas gdy inne są czysto zarządzane implementacje. Nie musisz być ekspertem w kryptografii, aby korzystać z tych klas. Podczas tworzenia nowego wystąpienia jednej z klas algorytmu szyfrowania klucze są generowane automatycznie w celu ułatwienia użycia, a właściwości domyślne są tak bezpieczne, jak to możliwe.

Ten przegląd zawiera streszczenie metod szyfrowania i praktyk obsługiwanych przez program .NET Framework, w tym obsługę manifestów ClickOnce, suite B i kryptografię nowej generacji (CNG) wprowadzone w programach .NET Framework 3.5.

Aby uzyskać dodatkowe informacje dotyczące kryptografii oraz usług, składników i narzędzi firmy Microsoft, które umożliwiają dodawanie zabezpieczeń kryptograficznych do aplikacji, zobacz sekcję Win32 i COM Development, Security w tej dokumentacji.

## <a name="cryptographic-primitives"></a>Prymitywy kryptograficzne

W typowej sytuacji, w której używana jest kryptografia, dwie strony (Alicja i Robert) komunikują się za działać za działam niezabezpieczonym kanałem. Alicja i Bob chcą zapewnić, że ich komunikacja pozostaje niezrozumiała dla każdego, kto może słuchać. Ponadto, ponieważ Alicja i Robert znajdują się w odległych lokalizacjach, Alicja musi upewnić się, że informacje, które otrzymuje od Roberta, nie zostały zmodyfikowane przez nikogo podczas transmisji. Ponadto musi upewnić się, że informacje naprawdę pochodzą od Boba, a nie od kogoś, kto podszywa się pod Boba.

Kryptografia służy do osiągnięcia następujących celów:

- Poufność: aby chronić tożsamość lub dane użytkownika przed ich odczytaniem.

- Integralność danych: aby chronić dane przed zmianą.

- Uwierzytelnianie: aby upewnić się, że dane pochodzą od określonej strony.

- Brak odrzucenia: aby uniemożliwić określonej stronie odmówienie, że wysłałwiadomość.

Aby osiągnąć te cele, można użyć kombinacji algorytmów i praktyk znanych jako prymitywy kryptograficzne, aby utworzyć schemat kryptograficzny. W poniższej tabeli wymieniono prymitywy kryptograficzne i ich zastosowania.

|Prymityw kryptograficzny|Użycie|
|-----------------------------|---------|
|Szyfrowanie kluczem tajnym (kryptografia symetryczna)|Wykonuje transformację danych, aby zaradzić ich odczytaniu przez osoby trzecie. Ten typ szyfrowania używa jednego udostępnionego, tajnego klucza do szyfrowania i odszyfrowywania danych.|
|Szyfrowanie kluczem publicznym (kryptografia asymetryczna)|Wykonuje transformację danych, aby zaradzić ich odczytaniu przez osoby trzecie. Ten typ szyfrowania używa pary kluczy publicznych/prywatnych do szyfrowania i odszyfrowywania danych.|
|Podpisywanie kryptograficzne|Pomaga zweryfikować, że dane pochodzą od określonej strony, tworząc podpis cyfrowy, który jest unikatowy dla tej strony. Ten proces używa również funkcji mieszania.|
|Skróty kryptograficzne|Mapuje dane z dowolnej długości do sekwencji bajtów o stałej długości. Hasze są statystycznie unikalne; inna sekwencja dwubajtowa nie będzie mieszania do tej samej wartości.|

## <a name="secret-key-encryption"></a>Szyfrowanie klucza tajnego

Algorytmy szyfrowania klucza tajnego używają pojedynczego klucza tajnego do szyfrowania i odszyfrowywania danych. Klucz należy zabezpieczyć przed dostępem nieautoryzowanych agentów, ponieważ każda strona, która ma klucz, może go użyć do odszyfrowania danych lub zaszyfrowania własnych danych, twierdząc, że pochodzą od Ciebie.

Szyfrowanie kluczem tajnym jest również określane jako szyfrowanie symetryczne, ponieważ ten sam klucz jest używany do szyfrowania i odszyfrowywania. Algorytmy szyfrowania klucza tajnego są bardzo szybkie (w porównaniu z algorytmami klucza publicznego) i dobrze nadają się do wykonywania przekształceń kryptograficznych na dużych strumieniach danych. Asymetryczne algorytmy szyfrowania, takie jak RSA, są ograniczone matematycznie w ilości danych, które mogą szyfrować. Algorytmy szyfrowania symetrycznego zazwyczaj nie mają tych problemów.

Typ algorytmu klucza tajnego o nazwie szyfr bloku jest używany do szyfrowania jednego bloku danych naraz. Szyfry blokowe, takie jak Standard szyfrowania danych (DES), TripleDES i Advanced Encryption Standard (AES) w kryptografii przekształcają blok wejściowy *n* bajtów w blok wyjściowy zaszyfrowanych bajtów. Jeśli chcesz zaszyfrować lub odszyfrować sekwencję bajtów, musisz to zrobić blok po bloku. Ponieważ *n* jest mały (8 bajtów dla DES i TripleDES; 16 bajtów [domyślnie], 24 bajtów lub 32 bajtów dla AES), wartości danych, które są większe niż *n,* muszą być szyfrowane po jednym bloku naraz. Wartości danych, które są mniejsze niż *n* muszą zostać rozwinięte do *n,* aby mogły zostać przetworzone.

Jedną z prostych form szyfrowania blokowego jest tryb elektronicznego codebooka (EBC). Tryb EBC nie jest uważany za bezpieczny, ponieważ nie używa wektora inicjalizacji do zainicjowania pierwszego bloku zwykłego tekstu. Dla danego klucza tajnego *k*, prosty szyfr bloku, który nie używa wektora inicjalizacji zaszyfruje ten sam blok wejściowy zwykłego tekstu do tego samego bloku wyjściowego szyfru. W związku z tym jeśli masz zduplikowane bloki w strumieniu wpostaci zwykłego tekstu wejściowego, będziesz miał zduplikowane bloki w strumieniu danych wyjściowych szyfrowania tekstu. Te zduplikowane bloki wyjściowe ostrzegają nieautoryzowanych użytkowników o słabym szyfrowaniu używanych algorytmów, które mogły być stosowane, oraz możliwych trybów ataku. Tryb szyfrowania EBC jest zatem dość podatny na analizy, a ostatecznie na kluczowe odkrycie.

Klasy szyfrowania bloków, które są dostarczane w bibliotece klas podstawowych, używają domyślnego trybu łańcuchowego zwanego łańcuchem szyfrowania blokowego (CBC), chociaż w razie potrzeby można zmienić tę wartość domyślną.

Szyfry CBC przezwyciężają problemy związane z szyframi EBC za pomocą wektora inicjalizacji (IV) do szyfrowania pierwszego bloku zwykłego tekstu. Każdy kolejny blok zwykłego tekstu przechodzi operację`XOR`wyłączności bitowej LUB ( ) z poprzednim blokiem szyfrującym, zanim zostanie zaszyfrowany. Każdy blok szyfru jest zatem zależny od wszystkich poprzednich bloków. Gdy ten system jest używany, typowe nagłówki komunikatów, które mogą być znane nieautoryzowanemu użytkownikowi, nie mogą być używane do odtwarzania klucza.

Jednym ze sposobów na złamanie zabezpieczeń danych zaszyfrowanych za pomocą szyfru CBC jest przeprowadzenie wyczerpującego wyszukiwania każdego możliwego klucza. W zależności od rozmiaru klucza, który jest używany do szyfrowania, tego rodzaju wyszukiwanie jest bardzo czasochłonne przy użyciu nawet najszybszych komputerów i dlatego jest niewykonalne. Większe rozmiary kluczy są trudniejsze do odszyfrowania. Chociaż szyfrowanie nie sprawia, że teoretycznie niemożliwe dla przeciwnika, aby pobrać zaszyfrowane dane, to nie podnieść koszt ten sposób. Jeśli wykonanie wyczerpującego wyszukiwania w celu pobrania danych ma znaczenie tylko przez kilka dni, wyczerpująca metoda wyszukiwania jest niepraktyczna.

Wadą szyfrowania klucza tajnego jest to, że zakłada, że dwie strony uzgodniły klucz i IV, i komunikował swoje wartości. IV nie jest uważany za tajemnicę i mogą być przekazywane w postaci zwykłego tekstu z wiadomością. Jednak klucz musi być utrzymywany w tajemnicy przed nieautoryzowanymi użytkownikami. Z powodu tych problemów szyfrowanie klucza tajnego jest często używane razem z szyfrowaniem klucza publicznego do prywatnej komunikacji wartości klucza i IV.

Zakładając, że Alicja i Robert są dwie strony, które chcą komunikować się za pomocą kanału niezabezpieczonego, mogą używać szyfrowania klucza tajnego w następujący sposób: Alicja i Robert zgadzają się użyć jednego określonego algorytmu (AES, na przykład) z określonym kluczem i IV. Alicja tworzy wiadomość i tworzy strumień sieciowy (być może nazwany potok lub sieciowy adres e-mail), na którym ma zostać wysłana wiadomość. Następnie szyfruje tekst przy użyciu klucza i IV i wysyła zaszyfrowaną wiadomość i IV do Roberta za pomocą intranetu. Robert odbiera zaszyfrowany tekst i odszyfrowuje go za pomocą IV i wcześniej uzgodniony klucz. Jeśli transmisja zostanie przechwycona, interceptor nie może odzyskać oryginalnej wiadomości, ponieważ nie zna klucza. W tym scenariuszu tylko klucz musi pozostać tajny. W scenariuszu rzeczywistym Alicja lub Robert generuje klucz tajny i używa szyfrowania klucza publicznego (asymetrycznego) do przenoszenia klucza tajnego (symetrycznego) do drugiej strony. Aby uzyskać więcej informacji na temat szyfrowania klucza publicznego, zobacz następną sekcję.

Program .NET Framework udostępnia następujące klasy implementujące algorytmy szyfrowania klucza tajnego:

- <xref:System.Security.Cryptography.AesManaged>(wprowadzony w .NET Framework 3.5).

- <xref:System.Security.Cryptography.DESCryptoServiceProvider>.

- <xref:System.Security.Cryptography.HMACSHA1>(Jest to technicznie algorytm klucztajny, ponieważ reprezentuje kod uwierzytelniania wiadomości, który jest obliczany przy użyciu funkcji skrótu kryptograficznego w połączeniu z kluczem tajnym. Zobacz [Wartości skrótów](#hash-values), w dalszej części tego tematu.)

- <xref:System.Security.Cryptography.RC2CryptoServiceProvider>.

- <xref:System.Security.Cryptography.RijndaelManaged>.

- <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>.

## <a name="public-key-encryption"></a>Szyfrowanie klucza publicznego

Szyfrowanie klucza publicznego używa klucza prywatnego, który musi być utrzymywany w tajemnicy przed nieautoryzowanymi użytkownikami i klucza publicznego, który może być upubliczniany dla każdego. Klucz publiczny i klucz prywatny są ze sobą matematycznie powiązane; dane szyfrowane przy użyciu klucza publicznego można odszyfrować tylko przy użyciu klucza prywatnego, a dane podpisane przy użyciu klucza prywatnego można zweryfikować tylko przy użyciu klucza publicznego. Klucz publiczny może być udostępniony każdemu; służy do szyfrowania danych, które mają być wysyłane do posiadacza klucza prywatnego. Algorytmy kryptograficzne klucza publicznego są również nazywane algorytmami asymetrycznymi, ponieważ do szyfrowania danych wymagany jest jeden klucz, a do odszyfrowania danych wymagany jest inny klucz. Podstawowa reguła kryptograficzna zabrania ponownego użycia kluczy, a oba klucze powinny być unikatowe dla każdej sesji komunikacji. Jednak w praktyce klucze asymetryczne są na ogół długotrwałe.

Dwie strony (Alicja i Robert) mogą używać szyfrowania klucza publicznego w następujący sposób: Po pierwsze, Alicja generuje parę kluczy publicznych/prywatnych. Jeśli Bob chce wysłać Alicji zaszyfrowaną wiadomość, prosi ją o jej klucz publiczny. Alicja wysyła Boba kluczem publicznym za pomocą niezabezpieczonej sieci, a Robert używa tego klucza do szyfrowania wiadomości. Bob wysyła zaszyfrowaną wiadomość do Alicji, a ona odszyfrowuje ją przy użyciu jej klucza prywatnego. Jeśli Robert odebrał klucz Alicji za działać za działaniom niezabezpieczonym, takim jak sieć publiczna, Robert jest otwarty na atak typu man-in-the-middle. W związku z tym Bob musi sprawdzić z Alice, że ma poprawną kopię jej klucza publicznego.

Podczas transmisji klucza publicznego Alicji nieautoryzowany agent może przechwycić klucz. Ponadto ten sam agent może przechwycić zaszyfrowaną wiadomość od Roberta. Jednak agent nie może odszyfrować wiadomości za pomocą klucza publicznego. Wiadomość można odszyfrować tylko przy pomocą klucza prywatnego Alicji, który nie został przesłany. Alicja nie używa swojego klucza prywatnego do szyfrowania wiadomości odpowiedzi do Roberta, ponieważ każdy, kto ma klucz publiczny, może odszyfrować wiadomość. Jeśli Alicja chce wysłać wiadomość z powrotem do Roberta, prosi Roberta o jego klucz publiczny i szyfruje jej wiadomość przy użyciu tego klucza publicznego. Następnie Robert odszyfrowuje wiadomość przy użyciu powiązanego z nim klucza prywatnego.

W tym scenariuszu Alicja i Robert używają szyfrowania klucza publicznego (asymetrycznego) do przenoszenia klucza tajnego (symetrycznego) i używania szyfrowania klucza tajnego przez pozostałą część sesji.

Poniższa lista zawiera porównania między algorytmami kryptograficznymi klucza publicznego i klucza tajnego:

- Algorytmy kryptograficzne klucza publicznego używają stałego rozmiaru buforu, podczas gdy algorytmy kryptograficzne klucza tajnego używają buforu o zmiennej długości.

- Algorytmów klucza publicznego nie można używać do łączenia danych w strumienie w sposób algorytmów klucza tajnego, ponieważ można szyfrować tylko niewielkie ilości danych. W związku z tym operacje asymetryczne nie używają tego samego modelu przesyłania strumieniowego jako operacji symetrycznych.

- Szyfrowanie klucza publicznego ma znacznie większą przestrzeń klucza (zakres możliwych wartości dla klucza) niż szyfrowanie klucza tajnego. W związku z tym szyfrowanie klucza publicznego jest mniej podatne na wyczerpujące ataki, które próbują każdy możliwy klucz.

- Klucze publiczne są łatwe do dystrybucji, ponieważ nie muszą być zabezpieczone, pod warunkiem, że istnieje jakiś sposób, aby zweryfikować tożsamość nadawcy.

- Niektóre algorytmy klucza publicznego (takie jak RSA i DSA, ale nie Diffie-Hellman) mogą być używane do tworzenia podpisów cyfrowych w celu zweryfikowania tożsamości nadawcy danych.

- Algorytmy klucza publicznego są bardzo powolne w porównaniu z algorytmami klucza tajnego i nie są przeznaczone do szyfrowania dużych ilości danych. Algorytmy klucza publicznego są przydatne tylko do przesyłania bardzo małych ilości danych. Zazwyczaj szyfrowanie klucza publicznego jest używane do szyfrowania klucza i IV do użycia przez algorytm klucza tajnego. Po przesłaniu klucza i IV szyfrowanie klucza tajnego jest używane przez pozostałą część sesji.

Program .NET Framework udostępnia następujące klasy implementujące algorytmy szyfrowania klucza publicznego:

- <xref:System.Security.Cryptography.DSACryptoServiceProvider>

- <xref:System.Security.Cryptography.RSACryptoServiceProvider>

- <xref:System.Security.Cryptography.ECDiffieHellman>(klasa podstawowa)

- <xref:System.Security.Cryptography.ECDiffieHellmanCng>

- <xref:System.Security.Cryptography.ECDiffieHellmanCngPublicKey>(klasa podstawowa)

- <xref:System.Security.Cryptography.ECDiffieHellmanKeyDerivationFunction>(klasa podstawowa)

- <xref:System.Security.Cryptography.ECDsaCng>

RSA umożliwia zarówno szyfrowanie, jak i podpisywanie, ale DSA może być używany tylko do podpisywania, a Diffie-Hellman może być używany tylko do generowania kluczy. Ogólnie rzecz biorąc algorytmy klucza publicznego są bardziej ograniczone w ich zastosowaniach niż algorytmy klucza prywatnego.

## <a name="digital-signatures"></a>Podpisy cyfrowe

Algorytmy klucza publicznego mogą być również używane do tworzenia podpisów cyfrowych. Podpisy cyfrowe uwierzytelniają tożsamość nadawcy (jeśli ufasz kluczowi publicznemu nadawcy) i pomagają chronić integralność danych. Przy użyciu klucza publicznego wygenerowanego przez Alicję odbiorca danych Alicji może sprawdzić, czy Alicja wysłała go, porównując podpis cyfrowy z danymi Alicji i kluczem publicznym Alicji.

Aby użyć kryptografii klucza publicznego do cyfrowego podpisania wiadomości, Alicja najpierw stosuje algorytm mieszania do wiadomości, aby utworzyć podsumowanie wiadomości. Podsumowanie wiadomości jest zwartą i unikalną reprezentacją danych. Alice następnie szyfruje skrót wiadomości za pomocą klucza prywatnego, aby utworzyć jej osobisty podpis. Po otrzymaniu wiadomości i podpisu, Bob odszyfrowuje podpis przy użyciu klucza publicznego Alice, aby odzyskać podsumowanie wiadomości i skróty wiadomości przy użyciu tego samego algorytmu mieszania, który Alice używane. Jeśli podsumowanie wiadomości, które Bob oblicza dokładnie pasuje do skrótu wiadomości odebrane od Alicji, Bob jest pewny, że wiadomość pochodzi od posiadacza klucza prywatnego i że dane nie zostały zmodyfikowane. Jeśli Bob ufa, że Alicja jest posiadaczem klucza prywatnego, wie, że wiadomość pochodzi od Alicji.

> [!NOTE]
> Podpis może zostać zweryfikowany przez każdego, ponieważ klucz publiczny nadawcy jest powszechnie znany i zazwyczaj znajduje się w formacie podpisu cyfrowego. Ta metoda nie zachowuje tajemnicy wiadomości; aby wiadomość była tajna, musi być również szyfrowana.

Program .NET Framework udostępnia następujące klasy implementowane algorytmy podpisu cyfrowego:

- <xref:System.Security.Cryptography.DSACryptoServiceProvider>

- <xref:System.Security.Cryptography.RSACryptoServiceProvider>

- <xref:System.Security.Cryptography.ECDsa>(klasa podstawowa)

- <xref:System.Security.Cryptography.ECDsaCng>

## <a name="hash-values"></a>Wartości mieszania

Algorytmy mieszania mapują wartości binarne o dowolnej długości na mniejsze wartości binarne o stałej długości, nazywane wartościami mieszania. Wartość mieszania jest liczbową reprezentacją fragmentu danych. Jeśli zdasz akapit zwykłego tekstu i zmienisz nawet jedną literę akapitu, kolejny skrót przyda inną wartość. Jeśli skrót jest kryptograficznie silny, jego wartość znacznie się zmieni. Na przykład jeśli jeden bit wiadomości zostanie zmieniony, funkcja silnego mieszania może generować dane wyjściowe, które różnią się o 50 procent. Wiele wartości wejściowych może mieszania do tej samej wartości wyjściowej. Jednak jest obliczeniowo niewykonalne, aby znaleźć dwa różne dane wejściowe, które mieszania do tej samej wartości.

Dwie strony (Alicja i Robert) można użyć funkcji mieszania w celu zapewnienia integralności wiadomości. Będą wybierać algorytm mieszania do podpisywania wiadomości. Alicja będzie pisać wiadomość, a następnie utworzyć skrót tej wiadomości przy użyciu wybranego algorytmu. Następnie będą stosować jedną z następujących metod:

- Alicja wysyła wiadomość w postaci zwykłego tekstu i komunikat haszowany (podpis cyfrowy) do Roberta. Robert odbiera i haszuje wiadomość i porównuje jego wartość mieszania z wartością mieszania, którą otrzymał od Alicji. Jeśli wartości mieszania są identyczne, wiadomość nie została zmieniona. Jeśli wartości nie są identyczne, wiadomość została zmieniona po alice napisał go.

  Niestety, ta metoda nie ustanawia autentyczności nadawcy. Każdy może podszyć się pod Alicję i wysłać wiadomość do Roberta. Mogą używać tego samego algorytmu mieszania do podpisywania wiadomości, a wszystkie Bob można określić, że wiadomość pasuje do jego podpisu. Jest to jedna z form ataku typu man-in-the-middle. Aby uzyskać więcej informacji, zobacz [Cryptography Next Generation (CNG) Secure Communication Example](https://docs.microsoft.com/previous-versions/cc488018(v=vs.100)).

- Alicja wysyła wiadomość w postaci zwykłego tekstu do Roberta za pomocą niezabezpieczonego kanału publicznego. Wysyła komunikat haszyszu do Roberta za dużo za dużo za pandoła kanału prywatnego. Robert odbiera wiadomość w postaci zwykłego tekstu, hashes go i porównuje skrót do prywatnie wymieniane hash. Jeśli haszysz pasuje, Bob wie dwie rzeczy:

  - Wiadomość nie została zmieniona.

  - Nadawca wiadomości (Alicja) jest autentyczny.

  Aby ten system działał, Alicja musi ukryć swoją oryginalną wartość skrótu ze wszystkich stron z wyjątkiem Boba.

- Alicja wysyła wiadomość w postaci zwykłego tekstu do Roberta za pośrednictwem niezabezpieczonego kanału publicznego i umieszcza zahaszoną wiadomość w jej publicznie widocznej witrynie sieci Web.

  Ta metoda zapobiega manipulowaniu wiadomościami, uniemożliwiając komukolwiek modyfikowanie wartości mieszania. Mimo że wiadomość i jej skrót mogą być odczytywane przez każdego, wartość mieszania może być zmieniona tylko przez Alicja. Osoba atakująca, która chce podszyć się pod Alicję, będzie wymagać dostępu do witryny sieci Web Alicji.

Żadna z poprzednich metod nie uniemożliwi komuś czytania wiadomości Alicji, ponieważ są one przesyłane w postaci zwykłego tekstu. Pełne zabezpieczenia zazwyczaj wymagają podpisów cyfrowych (podpisywania wiadomości) i szyfrowania.

.NET Framework zawiera następujące klasy, które implementują algorytmy mieszania:

- <xref:System.Security.Cryptography.HMACSHA1>.

- <xref:System.Security.Cryptography.MACTripleDES>.

- <xref:System.Security.Cryptography.MD5CryptoServiceProvider>.

- <xref:System.Security.Cryptography.RIPEMD160>.

- <xref:System.Security.Cryptography.SHA1Managed>.

- <xref:System.Security.Cryptography.SHA256Managed>.

- <xref:System.Security.Cryptography.SHA384Managed>.

- <xref:System.Security.Cryptography.SHA512Managed>.

- Warianty HMAC wszystkich algorytmów bezpiecznego algorytmu mieszania (SHA), Message Digest 5 (MD5) i RIPEMD-160.

- Implementacje CryptoServiceProvider (otoki kodu zarządzanego) wszystkich algorytmów SHA.

- Implementacje kryptografii nowej generacji (CNG) wszystkich algorytmów MD5 i SHA.

> [!NOTE]
> Wady projektowe MD5 zostały odkryte w 1996 roku, a zamiast tego zalecano SHA-1. W 2004 r. odkryto dodatkowe wady, a algorytm MD5 nie jest już uważany za bezpieczny. Algorytm SHA-1 również został uznany za niepewny, a sha-2 jest teraz zalecane zamiast tego.

## <a name="random-number-generation"></a>Generowanie liczb losowych

Generowanie liczb losowych jest integralną częścią wielu operacji kryptograficznych. Na przykład klucze kryptograficzne muszą być tak losowe, jak to możliwe, aby można było je odtworzyć. Generatory liczb losowych kryptograficznych muszą generować dane wyjściowe, które są obliczeniowo niewykonalne do przewidzenia z prawdopodobieństwem, które jest lepsze niż połowa. W związku z tym każda metoda przewidywania następnego bitu danych wyjściowych nie może działać lepiej niż zgadywanie losowe. Klasy w platformie .NET Framework używają generatorów liczb losowych do generowania kluczy kryptograficznych.

Klasa <xref:System.Security.Cryptography.RNGCryptoServiceProvider> jest implementacją algorytmu generatora liczb losowych.

## <a name="clickonce-manifests"></a>ClickOnce Manifesty

W .NET Framework 3.5 następujące klasy kryptografii umożliwiają uzyskiwanie i weryfikowanie informacji o podpisach manifestu dla aplikacji wdrożonych przy użyciu [technologii ClickOnce:](/visualstudio/deployment/clickonce-security-and-deployment)

- Klasa <xref:System.Security.Cryptography.ManifestSignatureInformation> uzyskuje informacje o podpismanifestu <xref:System.Security.Cryptography.ManifestSignatureInformation.VerifySignature%2A> podczas korzystania z jego przeciążenia metody.

- Można użyć <xref:System.Security.ManifestKinds> wyliczenia, aby określić, które manifesty do weryfikacji. Wynik weryfikacji jest jedną z <xref:System.Security.Cryptography.SignatureVerificationResult> wartości wyliczenia.

- Klasa <xref:System.Security.Cryptography.ManifestSignatureInformationCollection> zawiera tylko do odczytu <xref:System.Security.Cryptography.ManifestSignatureInformation> kolekcji obiektów zweryfikowanych podpisów.

 Ponadto następujące klasy zawierają szczegółowe informacje o podpisie:

- <xref:System.Security.Cryptography.StrongNameSignatureInformation>zawiera informacje o podpisie silnej nazwy manifestu.

- <xref:System.Security.Cryptography.X509Certificates.AuthenticodeSignatureInformation>reprezentuje informacje o podpisie Authenticode dla manifestu.

- <xref:System.Security.Cryptography.X509Certificates.TimestampInformation>zawiera informacje o sygnaturze czasowej na podpisie Authenticode.

- <xref:System.Security.Cryptography.X509Certificates.TrustStatus>zapewnia prosty sposób sprawdzenia, czy podpis Authenticode jest zaufany.

## <a name="suite-b-support"></a>Pomoc techniczna aplikacji Suite B

.NET Framework 3.5 obsługuje zestaw algorytmów kryptograficznych Suite B opublikowany przez Agencję Bezpieczeństwa Narodowego (NSA). Aby uzyskać więcej informacji na temat pakietu Suite B, zobacz [arkusz informacyjny kryptografii NSA Suite B](https://www.nsa.gov/what-we-do/information-assurance/).

Uwzględniono następujące algorytmy:

- Algorytm Advanced Encryption Standard (AES) o rozmiarach kluczy 128, 192 i 256 bitów do szyfrowania.

- Bezpieczne algorytmy mieszania SHA-1, SHA-256, SHA-384 i SHA-512 do mieszania. (Trzy ostatnie są zazwyczaj zgrupowane razem i określane jako SHA-2).)

- Algorytm podpisu cyfrowego krzywej elliptycznej (ECDSA) przy użyciu krzywych 256-bitowych, 384-bitowych i 521-bitowych moduli prime do podpisywania. Dokumentacja NSA wyraźnie definiuje te krzywe i nazywa je P-256, P-384 i P-521. Ten algorytm jest <xref:System.Security.Cryptography.ECDsaCng> dostarczany przez klasę. Umożliwia podpisywanie przy pomocą klucza prywatnego i weryfikowanie podpisu przy pomocą klucza publicznego.

- Algorytm Ellipttic Curve Diffie-Hellman (ECDH) przy użyciu krzywych 256-bitowych, 384-bitowych i 521-bitowych moduli prime do wymiany kluczy i tajnej umowy. Ten algorytm jest <xref:System.Security.Cryptography.ECDiffieHellmanCng> dostarczany przez klasę.

Otoki kodu zarządzanego dla implementacji certyfikatów Federal Information Processing Standard (FIPS) implementacji implementacji AES, SHA-256, SHA-384 i SHA-512 <xref:System.Security.Cryptography.AesCryptoServiceProvider>są dostępne w nowych <xref:System.Security.Cryptography.SHA256CryptoServiceProvider>, , <xref:System.Security.Cryptography.SHA384CryptoServiceProvider>i <xref:System.Security.Cryptography.SHA512CryptoServiceProvider> klas.

## <a name="cryptography-next-generation-cng-classes"></a>Klasy kryptografii nowej generacji (CNG)

Klasy Kryptografii nowej generacji (CNG) zapewniają zarządzane otoki wokół natywnych funkcji CNG. (CNG jest zamiennikiem CryptoAPI.) Klasy te mają "Cng" jako część ich nazw. Central do klas otoki <xref:System.Security.Cryptography.CngKey> CNG jest klasa kontenera kluczy, który abstrakcje przechowywania i używania kluczy CNG. Ta klasa umożliwia bezpieczne przechowywanie pary kluczy lub klucza publicznego i odwoływanie się do niej przy użyciu prostej nazwy ciągu. Eliptyczna klasa podpisu oparta <xref:System.Security.Cryptography.ECDsaCng> <xref:System.Security.Cryptography.ECDiffieHellmanCng> na krzywej <xref:System.Security.Cryptography.CngKey> i klasa szyfrowania mogą używać obiektów.

Klasa <xref:System.Security.Cryptography.CngKey> jest używana do różnych dodatkowych operacji, w tym otwierania, tworzenia, usuwania i eksportowania kluczy. Zapewnia również dostęp do podstawowego dojścia klucza do użycia podczas wywoływania funkcji macierzystych bezpośrednio.

.NET Framework 3.5 zawiera również wiele obsługujących klas CNG, takich jak następujące:

- <xref:System.Security.Cryptography.CngProvider>utrzymuje dostawcę magazynu kluczy.

- <xref:System.Security.Cryptography.CngAlgorithm>utrzymuje algorytm CNG.

- <xref:System.Security.Cryptography.CngProperty>zachowuje często używane właściwości klucza.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Model kryptografii](../../../docs/standard/security/cryptography-model.md)|Opisuje sposób implementacji kryptografii w bibliotece klas podstawowych.|
|[Przewodnik: tworzenie aplikacji kryptograficznej](../../../docs/standard/security/walkthrough-creating-a-cryptographic-application.md)|Demonstruje podstawowe zadania szyfrowania i odszyfrowywania.|
|[Konfigurowanie klas kryptografii](../../../docs/framework/configure-apps/configure-cryptography-classes.md)|Opisuje sposób mapowania nazw algorytmów na klasy kryptograficzne i mapowania identyfikatorów obiektów na algorytm kryptograficzny.|
