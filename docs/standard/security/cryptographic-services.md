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
- decryptioin [.NET Framework]
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
ms.openlocfilehash: f8193932deac3854b07085cba9faac76e68c4da8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cryptographic-services"></a>Usługi kryptograficzne
<a name="top"></a> Sieci publicznych, takich jak Internet nie udostępniają sposób zapewnienia bezpiecznej komunikacji między jednostkami. Komunikacja za pośrednictwem tych sieci jest podatny na odczytu lub nawet zmodyfikowane przez osoby nieupoważnione innych. Kryptografia ułatwia ochronę danych przed wyświetlaniem, udostępnia metody wykrywania, czy dane zostały zmodyfikowane, a także umożliwia bezpiecznych metod komunikacji za pośrednictwem kanałów w przeciwnym razie niezabezpieczone. Na przykład danych można być szyfrowane przy użyciu algorytmu kryptograficznego, przekazywane w stanu zaszyfrowanego i później odszyfrowywany przez stronę przeznaczone. Jeśli innych firm przechwytuje zaszyfrowane dane, będzie trudne do odszyfrowania.  
  
 W programie .NET Framework, klas w <xref:System.Security.Cryptography?displayProperty=nameWithType> przestrzeni nazw zarządzać wieloma szczegółami kryptografii. Niektóre są otoki dla niezarządzanych API szyfrowania firmy Microsoft (CryptoAPI), a inne implementacje czysto zarządzanych. Nie trzeba przeprowadzać ekspertem w kryptografii używać tych klas. Podczas tworzenia nowego wystąpienia jednego z szyfrowania algorytmu klasy klucze są automatycznie wygenerowana dla łatwość użycia i domyślne właściwości to jako bezpieczne i bezpieczny, jak to możliwe.  
  
 Ten przegląd zawiera streszczenie metody szyfrowania i praktyk obsługiwane przez program .NET Framework, w tym manifestów ClickOnce, Suite B i obsługi kryptografii nowej generacji (CNG) wprowadzone w systemach [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)].  
  
 Ten przegląd zawiera następujące sekcje:  
  
-   [Elementy podstawowe kryptograficznych](#primitives)  
  
-   [Szyfrowanie klucza tajnego](#secret_key)  
  
-   [Public-Key Encryption](#public_key)  
  
-   [Podpisy cyfrowe](#digital_signatures)  
  
-   [Wartości skrótu](#hash_values)  
  
-   [Generowanie liczby losowej](#random_numbers)  
  
-   [Manifesty ClickOnce](#clickonce)  
  
-   [Obsługa pakietu Suite B](#suite_b)  
  
-   [Tematy pokrewne](#related_topics)  
  
 Aby uzyskać dodatkowe informacje o kryptografii i usług firmy Microsoft, składniki i narzędzia, które umożliwiają dodanie zabezpieczeń kryptograficznych dla poszczególnych aplikacji Zobacz Win32 i COM Development sekcji zabezpieczeń w niniejszej dokumentacji.  
  
<a name="primitives"></a>   
## <a name="cryptographic-primitives"></a>Elementy podstawowe kryptograficznych  
 W przypadku typowych gdzie są używane kryptografii obie strony (Alicja i Robert) komunikacji za pośrednictwem niezabezpieczonych kanału. Alicja i Robert chcesz zapewnić incomprehensible każdego, kto może nasłuchiwać komunikacji. Ponadto ponieważ Alicja i Robert znajdują się w lokalizacjach zdalnych, Alicja musi upewnić się, że informacje, które użytkownik otrzymuje od Roberta, który nie został zmodyfikowany przez każdego podczas przesyłania. Ponadto użytkownik należy się upewnić, że informacje naprawdę pochodzą z niego, a nie z osoby, która personifikuje Roberta.  
  
 Kryptografia jest używana w następujących celach:  
  
-   Poufność: W celu ochrony przed odczytaniem tożsamości użytkownika lub danych.  
  
-   Integralność: Aby chronić dane przed zmianami.  
  
-   Uwierzytelnianie: Aby upewnić się, że dane pochodzą od określonej strony.  
  
-   Niemożność wyparcia: Aby zapobiec odmawianie wysłał wiadomość określonej strony.  
  
 Na osiągnięcie tych celów, kombinację algorytmów i rozwiązań, znany jako podstawowych kryptograficznych służy do tworzenia schematu kryptograficznego. W poniższej tabeli wymieniono podstawowych usług kryptograficznych i ich zastosowań.  
  
|Element podstawowy kryptograficznych|Zastosowanie|  
|-----------------------------|---------|  
|Klucz tajny szyfrowania (Kryptografia symetryczna)|Wykonuje przekształcenie danych, aby zapobiec odczytywany przez osoby trzecie. Ten typ szyfrowania wykorzystuje pojedynczy udostępniony, klucz tajny do szyfrowania i odszyfrowywania danych.|  
|Szyfrowanie klucza publicznego (kryptografii asymetrycznej)|Wykonuje przekształcenie danych, aby zapobiec odczytywany przez osoby trzecie. Ten typ szyfrowania używa pary kluczy publicznych/prywatnych do szyfrowania i odszyfrowywania danych.|  
|Kryptograficzne podpisywania|Pomaga sprawdzić pochodzą dane od strony określonej przez utworzenie podpis cyfrowy, który jest unikatowy dla tej strony. Ten proces wykorzystuje również funkcje skrótu.|  
|Skróty kryptograficzne|Mapuje dane z dowolnej długości do sekwencji bajtów o stałej długości. Skróty są statystycznie unikatowe; inną sekwencję dwubajtowego nie będzie skrótu na tę samą wartość.|  
  
 [Powrót do początku](#top)  
  
<a name="secret_key"></a>   
## <a name="secret-key-encryption"></a>Szyfrowanie klucza tajnego  
 Algorytmy szyfrowania klucza tajnego Użyj jednego klucza tajnego do szyfrowania i odszyfrowywania danych. Należy zabezpieczyć klucza z dostępu przez nieautoryzowanego agentów, ponieważ każda strona, która ma ten klucz służy do odszyfrowywania danych lub szyfrować dane, przejmowania się, że pochodzi on z należy.  
  
 Szyfrowania klucz tajny jest również nazywany szyfrowania symetrycznego, ponieważ ten sam klucz służy do szyfrowania i odszyfrowywania. Algorytmy szyfrowania klucz tajny są bardzo szybko (w porównaniu z algorytmy kluczy publicznych) i dobrze nadają się do operacji kryptograficznych przekształcenia na dużych strumieni danych. Szyfrowanie asymetryczne algorytmy, takich jak RSA są ograniczone ze sobą matematycznie w ilości danych może zaszyfrować. Algorytmy szyfrowania symetrycznego nie mają zwykle tych problemów.  
  
 Typ o nazwie szyfry blokowe algorytmu klucz tajny jest używany do szyfrowania jeden blok danych w czasie. Blok, takich jak standardowe DES (Data Encryption), TripleDES, szyfrowania i Advanced Encryption (Standard AES) kryptograficznie Przekształcanie wejściowego bloku *n* bajtów do bloku bajtów zaszyfrowanych danych wyjściowych. Jeśli chcesz zaszyfrować lub odszyfrować sekwencję bajtów, należy to robić blok po bloku. Ponieważ *n* jest mały (8 bajtów dla DES i TripleDES; 16 bajtów [domyślnie], bajtów 24 lub 32 bajtów AES), wartości danych, które są większe niż *n* muszą być szyfrowane jeden blok w czasie. Wartości danych, które są mniejsze niż *n* trzeba będzie dostosować do *n* aby mógł zostać przetworzony.  
  
 Jedna forma proste szyfry blokowe nosi nazwę trybu elektronicznych codebook (ECB). Tryb ECB jest uważana za niebezpieczną, ponieważ nie jest używane wektor inicjowania zainicjować pierwszego bloku w postaci zwykłego tekstu. Dla danego klucza tajnego *k*, szyfrowania Prosty blok, który nie używa wektor inicjowania są szyfrowane tego samego bloku wejściowych w postaci zwykłego tekstu w tym samym bloku danych wyjściowych tekstu szyfrowanego. W związku z tym jeśli masz zduplikowanych bloków w strumienia wejściowego w postaci zwykłego tekstu, konieczne będzie zduplikowanych bloków w danych wyjściowych strumienia tekstu szyfrowanego. Te bloki zduplikowany wyjściowy alertu nieautoryzowanym użytkownikom słabe szyfrowanie używane algorytmy, które mogą zastosować i trybów ataku. Trybu szyfrowania ECB występuje w związku z tym dość analizy, a ostatecznie klucza odnajdywania.  
  
 Klasy szyfrowania bloku, które znajdują się w bibliotece klasy podstawowej użyj domyślnego łańcucha tryb nazywany cipher block chaining (CBC), mimo że w razie potrzeby można zmienić to ustawienie domyślne.  
  
 Szyfry CBC uniknąć problemów związanych z szyfrowania ECB za pomocą wektora inicjowania (IV) do szyfrowania pierwszego bloku w postaci zwykłego tekstu. Każdy blok kolejnych zwykłego tekstu ulega logiczną lub wykluczające (`XOR`) operację z poprzedniego bloku tekstu szyfrowanego przed jest zaszyfrowany. Każdy blok tekstu szyfrowanego w związku z tym jest zależna od wszystkich poprzednich bloków. Gdy ten system jest nagłówki komunikatów używany, typowe, które nie mogą być nieautoryzowany użytkownik nie może być używany do odtwarzanie klucza.  
  
 Jednym ze sposobów danych zaszyfrowanego przy użyciu szyfrowania CBC jest przeprowadzenie kompleksowe przeszukiwanie każdej możliwe klucza. W zależności od rozmiaru klucza, który jest używany do szyfrowania tego rodzaju wyszukiwania jest bardzo czasochłonne, za pomocą nawet najszybszym komputerów i dlatego praktyce. Większe rozmiary klucza są trudniejsze do odszyfrowania. Chociaż szyfrowanie nie uniemożliwiają teoretycznie atakujący dokonuje pobierania zaszyfrowanych danych, jej podnieść koszt w ten sposób. Jeśli trwa trzech miesięcy do wykonania kompleksowe przeszukiwanie do pobierania danych, która ma znaczenie tylko przez kilka dni, metoda kompleksowe przeszukiwanie jest niepraktyczne.  
  
 Wadą szyfrowania klucz tajny jest zakłada obie strony mają uzgodniony klucza i IV i przekazywane ich wartości. IV nie jest uważana za klucz tajny i może być przekazywane w postaci zwykłego tekstu z komunikatem. Jednak klucz muszą być trzymane przed nieautoryzowanymi użytkownikami. Te problemy, klucz tajny szyfrowanie jest często używane razem z szyfrowania klucza publicznego do prywatnie komunikacji wartości klucza i IV.  
  
 Przy założeniu, że Alicja i Robert są obie strony chcą komunikują się za pośrednictwem kanału niezabezpieczone, szyfrowania klucza tajnego mogą użyć w następujący sposób: Alicja i Robert zobowiązuje się używać jeden algorytm konkretnego (na przykład AES) z określonym kluczem i IV. Alicja Redaguj komunikat i tworzy strumień sieciowych (prawdopodobnie nazwanego potoku lub sieci poczta e-mail) do przesyłania wiadomości. Następnie użytkownik szyfruje tekst przy użyciu klucza i IV i wysyła wiadomości i IV do niego za pośrednictwem sieci intranet. Robert otrzymuje zaszyfrowanego tekstu i odszyfrowuje ją przy użyciu IV i uprzednio uzgodniony klucza. Jeśli transmisja zostaje zatrzymana, interceptor nie można odzyskać oryginalnej wiadomości, ponieważ nie zna klucza. W tym scenariuszu tylko klucz musi pozostać poufne. W przypadku rzeczywistych Alicja lub Bob generuje klucz tajny i używa publicznego klucza szyfrowania (asymetrycznym) przenieść klucz tajny (symetrycznego) do drugiej strony. Aby uzyskać więcej informacji na temat szyfrowania klucza publicznego zobacz następną sekcję.  
  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Zawiera następujące klasy, które implementują algorytmów szyfrowania klucz tajny:  
  
-   <xref:System.Security.Cryptography.AesManaged> (wprowadzona w systemie [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)]).  
  
-   <xref:System.Security.Cryptography.DESCryptoServiceProvider>.  
  
-   <xref:System.Security.Cryptography.HMACSHA1> (Jest to technicznie algorytm klucza tajnego ponieważ reprezentuje ona kod uwierzytelniania wiadomości, która jest obliczana przy użyciu funkcji skrótu kryptograficznego, w połączeniu z kluczem tajnym. Zobacz [wartości skrótu](#hash_values)w dalszej części tego tematu.)  
  
-   <xref:System.Security.Cryptography.RC2CryptoServiceProvider>.  
  
-   <xref:System.Security.Cryptography.RijndaelManaged>.  
  
-   <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>.  
  
 [Powrót do początku](#top)  
  
<a name="public_key"></a>   
## <a name="public-key-encryption"></a>Public-Key Encryption  
 Szyfrowanie kluczy publicznych używa klucza prywatnego, który musi być trzymane przed nieautoryzowanymi użytkownikami i klucz publiczny, które mogą być ujawniane innym osobom. Klucz publiczny i klucz prywatny są ze sobą matematycznie powiązane; dane są szyfrowane przy użyciu klucza publicznego mogły być odszyfrowane tylko przy użyciu klucza prywatnego i danych, który jest podpisany przy użyciu klucza prywatnego można sprawdzić tylko przy użyciu klucza publicznego. Klucz publiczny mogą być udostępniane innym osobom; szyfrowanie danych służy do wysłania do posiadacz klucza prywatnego. Algorytmy kryptograficzne klucza publicznego są nazywane także asymetryczne algorytmy, ponieważ jeden klucz jest wymagany do szyfrowania danych, a inny klucz jest wymagany do odszyfrowania danych. Podstawowe reguły kryptograficznych uniemożliwia ponowne użycie klucza, a oba klucze powinna być unikatowa dla każdej sesji komunikacji. Jednak w praktyce, klucze asymetryczne są zazwyczaj długotrwałe.  
  
 Obie strony (Alicja i Robert) mogą używać szyfrowania klucza publicznego w następujący sposób: najpierw Alicja generuje pary kluczy publiczny/prywatny. Jeśli Bob chce wysłać wiadomość zaszyfrowaną Alicji, zwróci jej dla swojego klucza publicznego. Alicja wysyła Bob jej klucz publiczny za pośrednictwem niezabezpieczonej sieci, a Roberta, który używa tego klucza szyfrowania wiadomości. Robert wysyła zaszyfrowaną wiadomość do Alicji i klika odszyfrowuje je, używając swojego klucza prywatnego. Jeśli Bob Odebrano Alicji klucza kanałem niezabezpieczone, takich jak sieć publiczną Roberta, który jest otwarty na atak typu man-in--middle. W związku z tym Bob należy sprawdzić z Alicji, że ma on poprawny kopię swojego klucza publicznego.  
  
 Podczas przekazywania klucza publicznego Alicji nieautoryzowany agent może przechwycić klucza. Ponadto tego samego agenta może przechwycić zaszyfrowanego komunikatu z niego. Jednak agent nie może odszyfrować wiadomości z kluczem publicznym. Komunikat mogły być odszyfrowane tylko z klucza prywatnego Alicji, które nie zostały przekazane. Alicja nie używa jego klucz prywatny szyfrowania wiadomości odpowiedzi do niego, ponieważ każdy użytkownik z kluczem publicznym można odszyfrować wiadomości. Jeśli Alicja chce wysłać wiadomość do Roberta, użytkownik wprowadza Bob jego klucz publiczny i szyfruje jej wiadomości przy użyciu tego klucza publicznego. Robert odszyfrowuje komunikat przy użyciu jego skojarzony klucz prywatny.  
  
 W tym scenariuszu Alicja i Robert szyfrowania klucza publicznego (asymetryczne) transfer klucza tajnego (symetrycznego) do szyfrowania klucza tajnego w pozostałej części sesji.  
  
 Poniższa lista zawiera porównanie klucza publicznego i klucz tajny algorytmów kryptograficznych:  
  
-   Algorytmy kryptograficzne klucza publicznego Użyj stałego rozmiaru klucza tajnego algorytmy kryptograficzne używane buforu o zmiennej długości.  
  
-   Algorytmy kluczy publicznych nie może służyć do łańcucha danych razem do strumieni sposób można algorytmów klucza tajnego, ponieważ tylko małe ilości danych mogą być szyfrowane. W związku z tym asymetrycznego operacje nie należy używać tego samego modelu przesyłania strumieniowego jako operacje symetrycznego.  
  
-   Szyfrowanie klucza publicznego ma znacznie większe przestrzeni kluczy (zakres możliwych wartości dla klucza) niż szyfrowania klucza tajnego. Dlatego szyfrowanie klucza publicznego jest mniej podatny na ataki wyczerpująca, wypróbowania każdego klucza możliwe.  
  
-   Klucze publiczne są łatwe do dystrybucji, ponieważ nie mają być zabezpieczone, pod warunkiem, że istnieje jakiś sposób, aby sprawdzić tożsamość nadawcy.  
  
-   Niektóre algorytmy kluczy publicznych (np. RSA i DSA, ale nie Diffie-Hellman) może służyć do tworzenia podpisów cyfrowych, aby sprawdzić tożsamość nadawcy danych.  
  
-   Algorytmy klucza publicznego jest bardzo mała w porównaniu z algorytmów klucza tajnego, a nie są przeznaczone do szyfrowania dużych ilości danych. Algorytmy klucza publicznego są przydatne tylko w przypadku przenoszenia bardzo małe ilości danych. Zazwyczaj szyfrowania klucza publicznego jest używany do szyfrowania klucza i IV mają być używane przez algorytm klucza tajnego. Po przesłaniu klucza i IV klucz tajny klucz szyfrowania jest używany dla pozostałej części sesji.  
  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Zawiera następujące klasy, które implementują algorytmów szyfrowania klucza publicznego:  
  
-   <xref:System.Security.Cryptography.DSACryptoServiceProvider>  
  
-   <xref:System.Security.Cryptography.RSACryptoServiceProvider>  
  
-   <xref:System.Security.Cryptography.ECDiffieHellman> (klasa podstawowa)  
  
-   <xref:System.Security.Cryptography.ECDiffieHellmanCng>  
  
-   <xref:System.Security.Cryptography.ECDiffieHellmanCngPublicKey> (klasa podstawowa)  
  
-   <xref:System.Security.Cryptography.ECDiffieHellmanKeyDerivationFunction> (klasa podstawowa)  
  
-   <xref:System.Security.Cryptography.ECDsaCng>  
  
 RSA umożliwia szyfrowania i podpisywania, ale DSA można używać tylko w celu podpisywania, a Diffie-Hellman mogą służyć tylko do generowania kluczy. Ogólnie rzecz biorąc algorytmy kluczy publicznych jest coraz bardziej ograniczony w ich zastosowań niż algorytmów klucza prywatnego.  
  
 [Powrót do początku](#top)  
  
<a name="digital_signatures"></a>   
## <a name="digital-signatures"></a>Podpisy cyfrowe  
 Algorytmy klucza publicznego mogą służyć do tworzenia podpisów cyfrowych. Podpisy cyfrowe uwierzytelniania tożsamość nadawcy (Jeśli ufasz nadawcy klucz publiczny) oraz pomóc je zabezpieczyć integralność danych. Przy użyciu klucza publicznego, generowane przez Alicji, Odbiorca danych Alicji można sprawdzić Alicja wysłała go na podstawie porównania ilości podpis cyfrowy do Alicji danych i klucz publiczny Alicji.  
  
 Aby użyć kryptografii klucza publicznego do cyfrowego podpisywania wiadomości, Alicja najpierw dotyczy algorytmu wyznaczania wartości skrótu wiadomości, aby utworzyć skrót wiadomości. Skrót wiadomości jest compact i unikatowych reprezentację danych. Alicja następnie szyfruje skrót wiadomości za pomocą swojego klucza prywatnego, można utworzyć jej podpisu. Po otrzymaniu komunikatu i podpis, Roberta odszyfrowuje podpis odzyskać skrót wiadomości i wartości skrótu wiadomości przy użyciu tego samego algorytmu wyznaczania wartości skrótu używanego przez Alicja za pomocą klucza publicznego Alicji. Jeśli skrót wiadomości, że Bob oblicza dokładnie odpowiada skrót wiadomości otrzymanych od Alicji, Roberta, który zapewnia, że komunikat pochodzi z Właściciel klucza prywatnego i czy dane nie zostały zmodyfikowane. Jeśli Bob zaufania, że Alicja jest Właściciel klucza prywatnego, zna czy komunikat pochodzi z Alicji.  
  
> [!NOTE]
>  Ponieważ klucz publiczny nadawcy jest typowe wiedzy i zwykle znajduje się w formacie podpisu cyfrowego można sprawdzić podpisu dla wszystkich użytkowników. Ta metoda nie zachowuje poufności message; wiadomości tajne go musi również być szyfrowana.  
  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Zawiera następujące klasy, które implementują algorytmy podpisu cyfrowego:  
  
-   <xref:System.Security.Cryptography.DSACryptoServiceProvider>  
  
-   <xref:System.Security.Cryptography.RSACryptoServiceProvider>  
  
-   <xref:System.Security.Cryptography.ECDsa> (klasa podstawowa)  
  
-   <xref:System.Security.Cryptography.ECDsaCng>  
  
 [Powrót do początku](#top)  
  
<a name="hash_values"></a>   
## <a name="hash-values"></a>Wartości skrótu  
 Algorytmy wyznaczania wartości skrótu wartości binarnych o dowolnej długości są mapowane na mniejsze wartości binarnych o stałej długości, znany jako wartości skrótu. Wartość skrótu jest numeryczna reprezentacja elementu danych. Skrótów akapitu w postaci zwykłego tekstu i zmienić literę nawet jednego akapitu, kolejne skrótu powoduje wygenerowanie inną wartość. Jeśli wartość skrótu jest kryptograficznie silne, jego wartość zmieni się znacznie. Na przykład zmiana jednej ręki komunikat funkcji skrótu silne może powodować wyjścia, który różni się o 50%. Wiele wartości wejściowe mogą skrótu na tę samą wartość w danych wyjściowych. Jednak on jest praktycznie niemożliwe znaleźć dwóch różnych parametrów wejściowych ten skrót do tej samej wartości.  
  
 Obie strony (Alicja i Robert) można użyć funkcji skrótu do zapewnienia integralności komunikatu. Czy wybierają algorytmu wyznaczania wartości skrótu do podpisywania wiadomości. Alicja czy napisz wiadomość, a następnie utwórz skrót wiadomości przy użyciu wybranego algorytmu. One będzie następnie wykonaj jedną z następujących metod:  
  
-   Alicja wysyła komunikat w postaci zwykłego tekstu i skrótu wiadomości (podpisu cyfrowego) do niego. Robert otrzymuje i tworzy skrót wiadomości i porównuje jego wartość skrótu, aby wartość skrótu, które on odebrane z Alicja. Jeśli wartości skrótu są identyczne, wiadomość nie została zmieniona. Jeśli wartości nie są identyczne, wiadomości została zmieniona po Alicja zapisano go.  
  
     Niestety ta metoda nie ustanawia autentyczności nadawcy. Każda osoba, która personifikacji Alicja i wysyła komunikat do niego. Używają tego samego algorytmu wyznaczania wartości skrótu do podpisywania wiadomości i jest wszystkich Roberta, który można określić, czy komunikat odpowiada jego sygnatura. Jest to jedna forma ataku typu man-in--middle. Zobacz [NIB: przykład komunikacji Secure kryptografii nowej generacji (CNG)](https://msdn.microsoft.com/library/8048e94e-054a-417b-87c6-4f5e26710e6e) Aby uzyskać więcej informacji.  
  
-   Alicja wysyła wiadomości w postaci zwykłego tekstu do niego za pośrednictwem niezabezpieczonych kanału publicznego. Skrótu wiadomości użytkownik wysyła do niego za pośrednictwem bezpiecznego kanału prywatnych. Robert odbiera wiadomości w postaci zwykłego tekstu, jego skróty i porównuje skrót do prywatnie wymieniane wyznaczania wartości skrótu. Jeśli skróty są zgodne, Roberta, który zna dwie czynności:  
  
    -   Wiadomość nie została zmieniona.  
  
    -   Nadawca komunikatu (Anna) jest autentyczny.  
  
     Dla tego systemu do pracy Alicja należy ukryć jej oryginalnej wartości skrótu do wszystkich stron z wyjątkiem Roberta.  
  
-   Alicja wysyła wiadomości w postaci zwykłego tekstu do niego za pośrednictwem niezabezpieczonych kanału publicznego i umieszcza skrótu wiadomości w publicznie dostępnej witrynę sieci Web.  
  
     Ta metoda zapobiega próbom każda osoba, która uniemożliwia przy użyciu wartości skrótu wiadomości. Mimo że komunikat i jego skrót może zostać odczytany przez każdy użytkownik, wartość skrótu można zmienić tylko przez Alicji. Osoba atakująca, która chce personifikacji Alicja wymaga dostępu do witryny sieci Web Alicji.  
  
 Żadna z wcześniejszych metod uniemożliwi ktoś odczytywania Alicji wiadomości, ponieważ są one przekazywane w postaci zwykłego tekstu. Zabezpieczenia pełne wymaga zwykle od podpisów cyfrowych (podpisywanie komunikatów) i szyfrowania.  
  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Zawiera następujące klasy, które implementują algorytmów mieszania:  
  
-   <xref:System.Security.Cryptography.HMACSHA1>.  
  
-   <xref:System.Security.Cryptography.MACTripleDES>.  
  
-   <xref:System.Security.Cryptography.MD5CryptoServiceProvider>.  
  
-   <xref:System.Security.Cryptography.RIPEMD160>.  
  
-   <xref:System.Security.Cryptography.SHA1Managed>.  
  
-   <xref:System.Security.Cryptography.SHA256Managed>.  
  
-   <xref:System.Security.Cryptography.SHA384Managed>.  
  
-   <xref:System.Security.Cryptography.SHA512Managed>.  
  
-   Metoda HMAC wariantów wszystkich algorytmów Secure Hash Algorithm (SHA), Message Digest 5 (MD5) i RIPEMD 160.  
  
-   Implementacje CryptoServiceProvider (otoki kod zarządzany) algorytmów SHA.  
  
-   Implementacje wszystkich algorytmów MD5 i SHA do kryptografii nowej generacji (CNG).  
  
> [!NOTE]
>  Wady projektowe MD5 zostały odnalezione w 1996 i SHA-1 został zalecony, zamiast tego. 2004 dodatkowe wady zostały wykryte i algorytmu MD5 nie jest uznawane za bezpieczne. Również znaleziono algorytmu SHA-1 jako niebezpieczne i SHA-2 jest teraz zalecane zamiast tego.  
  
 [Powrót do początku](#top)  
  
<a name="random_numbers"></a>   
## <a name="random-number-generation"></a>Generowanie liczby losowej  
 Generowanie liczby losowej jest integralną częścią wielu operacji kryptograficznych. Na przykład kluczy kryptograficznych muszą być jako losowych, jak to możliwe, aby była możliwość ich odtworzenia. Kryptograficznych generatory liczb losowych należy wygenerować wyjściowy, który jest praktycznie niemożliwe do prognozowania z prawdopodobieństwo, że jest lepszym rozwiązaniem niż połowę. W związku z tym każda metoda przewidywania dalej bit danych wyjściowych nie należy wykonać lepszą wydajność niż odgadnięcie losowych. Klasy w [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] losowych liczb generatory umożliwia generowanie kluczy kryptograficznych.  
  
 <xref:System.Security.Cryptography.RNGCryptoServiceProvider> Klasa jest implementacją algorytmu generatora liczb losowych.  
  
 [Powrót do początku](#top)  
  
<a name="clickonce"></a>   
## <a name="clickonce-manifests"></a>Manifesty ClickOnce  
 W [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)], następujące klasy kryptografii pozwalają uzyskać i zweryfikować informacje o podpisów manifestu dla aplikacji, które są wdrażane za pomocą [technologii ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment):  
  
-   <xref:System.Security.Cryptography.ManifestSignatureInformation> Klas uzyskuje informacje o podpisie manifestu, korzystając z jego <xref:System.Security.Cryptography.ManifestSignatureInformation.VerifySignature%2A> przeciążenia metody.  
  
-   Można użyć <xref:System.Security.ManifestKinds> wyliczeniu, aby określić, które manifesty można zweryfikować. Wynik weryfikacji jest jednym z <xref:System.Security.Cryptography.SignatureVerificationResult> wartości wyliczenia.  
  
-   <xref:System.Security.Cryptography.ManifestSignatureInformationCollection> Klasa udostępnia kolekcję tylko do odczytu <xref:System.Security.Cryptography.ManifestSignatureInformation> obiektów zweryfikowano podpisów.  
  
 Ponadto następujące klasy zawierają informacje określonej sygnatury:  
  
-   <xref:System.Security.Cryptography.StrongNameSignatureInformation> Przechowuje informacje podpisu silnej nazwy dla manifest.  
  
-   <xref:System.Security.Cryptography.X509Certificates.AuthenticodeSignatureInformation> reprezentuje informacje o podpisie Authenticode dla manifest.  
  
-   <xref:System.Security.Cryptography.X509Certificates.TimestampInformation> zawiera informacje o sygnaturę czasową na podpis Authenticode.  
  
-   <xref:System.Security.Cryptography.X509Certificates.TrustStatus> zapewnia prosty sposób sprawdzić, czy podpis Authenticode jest zaufany.  
  
 [Powrót do początku](#top)  
  
<a name="suite_b"></a>   
## <a name="suite-b-support"></a>Obsługa pakietu Suite B  
 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] Obsługuje zestaw Suite B algorytmów kryptograficznych opublikowane przez National Security Agency (NSA). Aby uzyskać więcej informacji na temat pakietu Suite B, zobacz [NSA Suite B kryptografii zestawieniem](https://www.nsa.gov/what-we-do/information-assurance/).  
  
 Uwzględniono następujących algorytmów:  
  
-   Advanced Encryption Standard (AES) algorytmu klucza rozmiarach 128, 192 i 256 bitów do szyfrowania.  
  
-   Do tworzenia skrótów, należy zabezpieczyć algorytmów wyznaczania wartości skrótu SHA-1, SHA-256, SHA-384 i SHA-512. (Ostatnich trzech zazwyczaj zgrupowanych razem i nazywany SHA-2.)  
  
-   Eliptycznej krzywej Digital Signature Algorithm (ECDSA), za pomocą krzywych 256-bitowego, 384-bitowy i 521-bitowe moduli głównym do podpisywania. Dokumentacja NSA specjalnie definiuje te krzywych i wywołuje ich p-256, p-384 i p-521. Ten algorytm jest udostępniany przez <xref:System.Security.Cryptography.ECDsaCng> klasy. Umożliwia ona Zaloguj się przy użyciu klucza prywatnego i zweryfikować podpisu z kluczem publicznym.  
  
-   Eliptycznej algorytm krzywej Diffie-Hellmana (ECDH), przy użyciu krzywych 256-bitowego, 384-bitowy i 521-bitowe moduli prime wymiany kluczy oraz tajnej umowy. Ten algorytm jest udostępniany przez <xref:System.Security.Cryptography.ECDiffieHellmanCng> klasy.  
  
 Kod zarządzany otok dla przetwarzania Standard FIPS (Federal Information) certyfikowane implementacje implementacje AES, SHA-256, SHA-384 i SHA-512 są dostępne w nowym <xref:System.Security.Cryptography.AesCryptoServiceProvider>, <xref:System.Security.Cryptography.SHA256CryptoServiceProvider>, <xref:System.Security.Cryptography.SHA384CryptoServiceProvider>, i <xref:System.Security.Cryptography.SHA512CryptoServiceProvider> klasy.  
  
 [Powrót do początku](#top)  
  
<a name="cng"></a>   
## <a name="cryptography-next-generation-cng-classes"></a>Klasy Next Generation (CNG) kryptografii  
 Klasy kryptografii nowej generacji (CNG) podaj zarządzanych otokę funkcji CNG natywnych. (CNG jest zamiennikiem CryptoAPI). Te klasy mają "Cng" jako część nazwy. Centralnej do klasy otoki CNG jest <xref:System.Security.Cryptography.CngKey> klucz kontenera klasy, która abstracts magazynu i korzystania z kluczy CNG. Ta klasa pozwala bezpiecznie przechowywać pary kluczy lub klucza publicznego i odwołuje się do niego przy użyciu nazwy prostego ciągu. Eliptycznej opartej na krzywej <xref:System.Security.Cryptography.ECDsaCng> Klasa podpisu i <xref:System.Security.Cryptography.ECDiffieHellmanCng> służy klasa szyfrowania <xref:System.Security.Cryptography.CngKey> obiektów.  
  
 <xref:System.Security.Cryptography.CngKey> Klasa jest używana dla różnych dodatkowe operacje, w tym otwierania, tworzenie i eksportowanie kluczy. Umożliwia także dostęp do podstawowych dojścia klucza do użycia podczas bezpośrednie wywoływanie funkcji natywnych.  
  
 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] Różnych klas CNG, takich jak obsługa obejmuje również:  
  
-   <xref:System.Security.Cryptography.CngProvider> przechowuje dostawcy magazynu kluczy.  
  
-   <xref:System.Security.Cryptography.CngAlgorithm> obsługuje algorytm CNG.  
  
-   <xref:System.Security.Cryptography.CngProperty> utrzymuje często używanych właściwości klucza.  
  
 [Powrót do początku](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Model kryptografii](../../../docs/standard/security/cryptography-model.md)|W tym artykule opisano, jak kryptografii jest zaimplementowana w klasie podstawowej biblioteki.|  
|[Przewodnik: tworzenie aplikacji kryptograficznej](../../../docs/standard/security/walkthrough-creating-a-cryptographic-application.md)|Przedstawia podstawowe zadania szyfrowania i odszyfrowywania.|  
|[Konfigurowanie klas kryptografii](../../../docs/framework/configure-apps/configure-cryptography-classes.md)|Opisuje sposób mapowania nazw algorytmu kryptograficznego klas i mapowanie identyfikatorów obiektów na algorytmów kryptograficznych.|
