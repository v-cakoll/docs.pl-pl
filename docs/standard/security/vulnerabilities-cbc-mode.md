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
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a><span data-ttu-id="7d17d-103">Luki w zabezpieczeniach chronometrażu z odszyfrowywaniem symetrycznym w trybie CBC przy użyciu uzupełnienia</span><span class="sxs-lookup"><span data-stu-id="7d17d-103">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>

<span data-ttu-id="7d17d-104">Firma Microsoft uważa, że nie jest już bezpiecznie odszyfrowywać dane zaszyfrowane przy użyciu trybu szyfr-blocking (CBC) szyfrowania symetrycznego, gdy stosowane jest dopełnienie, bez uprzedniego zapewnienia integralności tekstu szyfrowanego, z wyjątkiem bardzo szczególnych rodzin.</span><span class="sxs-lookup"><span data-stu-id="7d17d-104">Microsoft believes that it's no longer safe to decrypt data encrypted with the Cipher-Block-Chaining (CBC) mode of symmetric encryption when verifiable padding has been applied without first ensuring the integrity of the ciphertext, except for very specific circumstances.</span></span> <span data-ttu-id="7d17d-105">Jest to orzeczenie oparte na aktualnie znanych badaniach kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="7d17d-105">This judgement is based on currently known cryptographic research.</span></span> 

## <a name="introduction"></a><span data-ttu-id="7d17d-106">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="7d17d-106">Introduction</span></span>

<span data-ttu-id="7d17d-107">Zapełnienie ataku Oracle jest typem ataków na zaszyfrowane dane, które umożliwiają atakującemu odszyfrowanie zawartości danych bez znajomości klucza.</span><span class="sxs-lookup"><span data-stu-id="7d17d-107">A padding oracle attack is a type of attack against encrypted data that allows the attacker to decrypt the contents of the data, without knowing the key.</span></span>

<span data-ttu-id="7d17d-108">Firma Oracle odnosi się do "powiedzieć", który zapewnia atakującemu informacje o tym, czy wykonywana akcja jest poprawna, czy nie.</span><span class="sxs-lookup"><span data-stu-id="7d17d-108">An oracle refers to a "tell" which gives an attacker information about whether the action they're executing is correct or not.</span></span> <span data-ttu-id="7d17d-109">Wyobraź sobie, że gra plansza lub karta jest połączona z elementem podrzędnym.</span><span class="sxs-lookup"><span data-stu-id="7d17d-109">Imagine playing a board or card game with a child.</span></span> <span data-ttu-id="7d17d-110">Gdy jej czołowa lampka ma duży uśmiech, ponieważ uzna, że jest to dobry ruch, to jest Oracle.</span><span class="sxs-lookup"><span data-stu-id="7d17d-110">When her face lights up with a big smile because she thinks she's about to make a good move, that's an oracle.</span></span> <span data-ttu-id="7d17d-111">Jako przeciwnik może użyć tego programu Oracle do zaplanowania odpowiednio następnego przejścia.</span><span class="sxs-lookup"><span data-stu-id="7d17d-111">You, as the opponent, can use this oracle to plan your next move appropriately.</span></span>

<span data-ttu-id="7d17d-112">Uzupełnienie jest określonym warunkiem kryptograficznym.</span><span class="sxs-lookup"><span data-stu-id="7d17d-112">Padding is a specific cryptographic term.</span></span> <span data-ttu-id="7d17d-113">Niektóre szyfry, które są algorytmami używanymi do szyfrowania danych, działają na blokach danych, w których każdy blok ma stały rozmiar.</span><span class="sxs-lookup"><span data-stu-id="7d17d-113">Some ciphers, which are the algorithms used to encrypt your data, work on blocks of data where each block is a fixed size.</span></span> <span data-ttu-id="7d17d-114">Jeśli dane, które mają zostać zaszyfrowane, nie są odpowiednim rozmiarem do wypełnienia bloków, dane są uzupełniane do momentu, w którym się nie robi.</span><span class="sxs-lookup"><span data-stu-id="7d17d-114">If the data you want to encrypt isn't the right size to fill the blocks, your data is padded until it does.</span></span> <span data-ttu-id="7d17d-115">Wiele form uzupełniania wymaga, aby uzupełnienie było zawsze obecne, nawet jeśli oryginalne dane wejściowe miały prawidłowy rozmiar.</span><span class="sxs-lookup"><span data-stu-id="7d17d-115">Many forms of padding require that padding to always be present, even if the original input was of the right size.</span></span> <span data-ttu-id="7d17d-116">Dzięki temu uzupełnianie będzie zawsze bezpiecznie usuwane podczas odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="7d17d-116">This allows the padding to always be safely removed upon decryption.</span></span>

<span data-ttu-id="7d17d-117">Jednoczesne umieszczenie obu tych elementów spowoduje, że implementacja oprogramowania z nieuzupełnieniem programu Oracle pokazuje, czy odszyfrowane dane mają prawidłowe uzupełnienie.</span><span class="sxs-lookup"><span data-stu-id="7d17d-117">Putting the two things together, a software implementation with a padding oracle reveals whether decrypted data has valid padding.</span></span> <span data-ttu-id="7d17d-118">Oracle może być coś prostej, ponieważ zwraca wartość "nieprawidłowe uzupełnienie" lub coś bardziej skomplikowanego, jak przetwarzać prawidłowy blok, w przeciwieństwie do nieprawidłowego bloku.</span><span class="sxs-lookup"><span data-stu-id="7d17d-118">The oracle could be something as simple as returning a value that says "Invalid padding" or something more complicated like taking a measurably different time to process a valid block as opposed to an invalid block.</span></span>

<span data-ttu-id="7d17d-119">Szyfry oparte na blokach mają inną właściwość o nazwie Mode, która określa relację danych w pierwszym bloku z danymi w drugim bloku itd.</span><span class="sxs-lookup"><span data-stu-id="7d17d-119">Block-based ciphers have another property, called the mode, which determines the relationship of data in the first block to the data in the second block, and so on.</span></span> <span data-ttu-id="7d17d-120">Jednym z najczęściej używanych trybów jest CBC.</span><span class="sxs-lookup"><span data-stu-id="7d17d-120">One of the most commonly used modes is CBC.</span></span> <span data-ttu-id="7d17d-121">CBC wprowadza początkowy losowy blok, znany jako wektor inicjujący (IV) i łączy poprzedni blok z wynikiem statycznego szyfrowania, aby uniemożliwić mu szyfrowanie tego samego komunikatu z tym samym kluczem, nie zawsze generują te same zaszyfrowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="7d17d-121">CBC introduces an initial random block, known as the Initialization Vector (IV), and combines the previous block with the result of static encryption to make it such that encrypting the same message with the same key doesn't always produce the same encrypted output.</span></span>

<span data-ttu-id="7d17d-122">Osoba atakująca może korzystać z uzupełniania oprogramowania Oracle, w połączeniu z CBC danych, w celu wysyłania nieco zmienionych komunikatów do kodu, który ujawnia oprogramowanie Oracle, a także do wysyłania danych do momentu, gdy firma Oracle poinformuje ich, że dane są poprawne.</span><span class="sxs-lookup"><span data-stu-id="7d17d-122">An attacker can use a padding oracle, in combination with how CBC data is structured, to send slightly changed messages to the code that exposes the oracle, and keep sending data until the oracle tells them the data is correct.</span></span> <span data-ttu-id="7d17d-123">Z tej odpowiedzi osoba atakująca może odszyfrować bajt komunikatu według bajtu.</span><span class="sxs-lookup"><span data-stu-id="7d17d-123">From this response, the attacker can decrypt the message byte by byte.</span></span>

<span data-ttu-id="7d17d-124">Nowoczesne sieci komputerowe mają taką wysoką jakość, którą atakujący może wykryć bardzo małe (mniej niż 0,1 ms) różnice w czasie wykonywania w systemach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="7d17d-124">Modern computer networks are of such high quality that an attacker can detect very small (less than 0.1 ms) differences in execution time on remote systems.</span></span><span data-ttu-id="7d17d-125"> Aplikacje, które zakładają, że pomyślne odszyfrowywanie może wystąpić tylko wtedy, gdy dane nie zostały naruszone, mogą być narażone na ataki z narzędzi, które są przeznaczone do zaobserwowania różnic w przypadku pomyślnego i nieudanego odszyfrowania.</span><span class="sxs-lookup"><span data-stu-id="7d17d-125"> Applications that are assuming that a successful decryption can only happen when the data wasn't tampered with may be vulnerable to attack from tools that are designed to observe differences in successful and unsuccessful decryption.</span></span> <span data-ttu-id="7d17d-126">Chociaż różnica czasu może być bardziej znacząca w niektórych językach lub bibliotekach niż inne, uważa się, że jest to praktyczne zagrożenie dla wszystkich języków i bibliotek, gdy odpowiedź aplikacji do awarii jest brana pod uwagę.</span><span class="sxs-lookup"><span data-stu-id="7d17d-126">While this timing difference may be more significant in some languages or libraries than others, it's now believed that this is a practical threat for all languages and libraries when the application's response to failure is taken into account.</span></span>

<span data-ttu-id="7d17d-127">Ten atak polega na możliwości zmiany zaszyfrowanych danych i przetestowania wyniku przy użyciu programu Oracle.</span><span class="sxs-lookup"><span data-stu-id="7d17d-127">This attack relies on the ability to change the encrypted data and test the result with the oracle.</span></span> <span data-ttu-id="7d17d-128">Jedynym sposobem na całkowite ograniczenie ataku jest wykrycie zmian zaszyfrowanych danych i odrzucenie wykonywania jakichkolwiek działań na nim.</span><span class="sxs-lookup"><span data-stu-id="7d17d-128">The only way to fully mitigate the attack is to detect changes to the encrypted data and refuse to perform any actions on it.</span></span> <span data-ttu-id="7d17d-129">Standardowy sposób to utworzenie podpisu dla danych i zweryfikowanie podpisu przed wykonaniem jakiejkolwiek operacji.</span><span class="sxs-lookup"><span data-stu-id="7d17d-129">The standard way to do this is to create a signature for the data and validate that signature before any operations are performed.</span></span> <span data-ttu-id="7d17d-130">Podpis musi być możliwy do zweryfikowania, nie może być utworzony przez osobę atakującą, w przeciwnym razie zmienia zaszyfrowane dane, a następnie oblicza nowy podpis na podstawie zmienionych danych.</span><span class="sxs-lookup"><span data-stu-id="7d17d-130">The signature must be verifiable, it cannot be created by the attacker, otherwise they'd change the encrypted data, then compute a new signature based on the changed data.</span></span> <span data-ttu-id="7d17d-131">Jeden wspólny typ odpowiedniej sygnatury jest znany jako kod uwierzytelniania wiadomości podwyższego poziomu (HMAC).</span><span class="sxs-lookup"><span data-stu-id="7d17d-131">One common type of appropriate signature is known as a keyed-hash message authentication code (HMAC).</span></span> <span data-ttu-id="7d17d-132">HMAC różni się od sumy kontrolnej w tym, że przyjmuje klucz tajny znany tylko osobie wytwarzającej kod HMAC i osobie sprawdzającej ją.</span><span class="sxs-lookup"><span data-stu-id="7d17d-132">An HMAC differs from a checksum in that it takes a secret key, known only to the person producing the HMAC and to the person validating it.</span></span> <span data-ttu-id="7d17d-133">Bez posiadania klucza nie można utworzyć poprawnego algorytmu HMAC.</span><span class="sxs-lookup"><span data-stu-id="7d17d-133">Without possession of the key, you can't produce a correct HMAC.</span></span> <span data-ttu-id="7d17d-134">Po otrzymaniu danych można wykonać zaszyfrowane dane, niezależnie od obliczenia algorytmu HMAC przy użyciu klucza tajnego i udziału nadawcy, a następnie porównać kod HMAC, który został wysłany na obliczony.</span><span class="sxs-lookup"><span data-stu-id="7d17d-134">When you receive your data, you'd take the encrypted data, independently compute the HMAC using the secret key you and the sender share, then compare the HMAC they sent against the one you computed.</span></span> <span data-ttu-id="7d17d-135">To porównanie musi być stałą godziną, w przeciwnym razie dodaliśmy kolejną wykrywalną wersję Oracle, co pozwala na atak innego typu.</span><span class="sxs-lookup"><span data-stu-id="7d17d-135">This comparison must be constant time, otherwise you've added another detectable oracle, allowing a different type of attack.</span></span>

<span data-ttu-id="7d17d-136">Podsumowując, aby bezpiecznie korzystać z uzupełnionych szyfrów CBC Block, należy połączyć je z HMAC (lub innym sprawdzaniem integralności danych), które są weryfikowane przy użyciu stałego porównania czasu przed próbą odszyfrowania danych.</span><span class="sxs-lookup"><span data-stu-id="7d17d-136">In summary, to use padded CBC block ciphers safely, you must combine them with an HMAC (or another data integrity check) that you validate using a constant time comparison before trying to decrypt the data.</span></span> <span data-ttu-id="7d17d-137">Ponieważ wszystkie zmienione komunikaty mają ten sam czas na wygenerowanie odpowiedzi, atak jest nieautoryzowany.</span><span class="sxs-lookup"><span data-stu-id="7d17d-137">Since all altered messages take the same amount time to produce a response, the attack is prevented.</span></span>

## <a name="who-is-vulnerable"></a><span data-ttu-id="7d17d-138">Kto jest narażony</span><span class="sxs-lookup"><span data-stu-id="7d17d-138">Who is vulnerable</span></span>

<span data-ttu-id="7d17d-139">Ta luka w zabezpieczeniach dotyczy zarówno aplikacji zarządzanych, jak i natywnych, które wykonują własne szyfrowanie i odszyfrowywanie.</span><span class="sxs-lookup"><span data-stu-id="7d17d-139">This vulnerability applies to both managed and native applications that are performing their own encryption and decryption.</span></span> <span data-ttu-id="7d17d-140">Dotyczy to na przykład:</span><span class="sxs-lookup"><span data-stu-id="7d17d-140">This includes, for example:</span></span>

- <span data-ttu-id="7d17d-141">Aplikacja, która szyfruje plik cookie na potrzeby późniejszego odszyfrowywania na serwerze.</span><span class="sxs-lookup"><span data-stu-id="7d17d-141">An application that encrypts a cookie for later decryption on the server.</span></span>
- <span data-ttu-id="7d17d-142">Aplikacja bazy danych, która zapewnia użytkownikom możliwość wstawiania danych do tabeli, której kolumny są później odszyfrowywane.</span><span class="sxs-lookup"><span data-stu-id="7d17d-142">A database application that provides the ability for users to insert data into a table whose columns are later decrypted.</span></span>
- <span data-ttu-id="7d17d-143">Aplikacja do transferu danych, która opiera się na szyfrowaniu przy użyciu klucza współużytkowanego do ochrony przesyłanych danych.</span><span class="sxs-lookup"><span data-stu-id="7d17d-143">A data transfer application that relies on encryption using a shared key to protect the data in transit.</span></span>
- <span data-ttu-id="7d17d-144">Aplikacja, która szyfruje i odszyfrowuje komunikaty "wewnątrz" tunelu TLS.</span><span class="sxs-lookup"><span data-stu-id="7d17d-144">An application that encrypts and decrypts messages "inside" the TLS tunnel.</span></span>

<span data-ttu-id="7d17d-145">Należy pamiętać, że użycie protokołu TLS sama może nie chronić w tych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="7d17d-145">Note that using TLS alone may not protect you in these scenarios.</span></span>

<span data-ttu-id="7d17d-146">Aplikacja podatna na ataki:</span><span class="sxs-lookup"><span data-stu-id="7d17d-146">A vulnerable application:</span></span>

- <span data-ttu-id="7d17d-147">Odszyfrowuje dane przy użyciu trybu szyfru CBC z możliwym do sprawdzenia trybem uzupełniania, takim jak PKCS # 7 lub ANSI X. 923.</span><span class="sxs-lookup"><span data-stu-id="7d17d-147">Decrypts data using the CBC cipher mode with a verifiable padding mode, such as PKCS#7 or ANSI X.923.</span></span>
- <span data-ttu-id="7d17d-148">Wykonuje odszyfrowywanie bez wykonywania kontroli integralności danych (za pośrednictwem komputera MAC lub asymetrycznego podpisu cyfrowego).</span><span class="sxs-lookup"><span data-stu-id="7d17d-148">Performs the decryption without having performed a data integrity check (via a MAC or an asymmetric digital signature).</span></span>

<span data-ttu-id="7d17d-149">Dotyczy to również aplikacji utworzonych na podstawie abstrakcji na podstawie tych elementów pierwotnych, takich jak struktura EnvelopedData składni wiadomości kryptograficznych (PKCS # 7/CMS).</span><span class="sxs-lookup"><span data-stu-id="7d17d-149">This also applies to applications built on top of abstractions over top of these primitives, such as the Cryptographic Message Syntax (PKCS#7/CMS) EnvelopedData structure.</span></span>

## <a name="related-areas-of-concern"></a><span data-ttu-id="7d17d-150">Powiązane obszary problemu</span><span class="sxs-lookup"><span data-stu-id="7d17d-150">Related areas of concern</span></span>

<span data-ttu-id="7d17d-151">Badania przeprowadziły do tego, że firma Microsoft może być bardziej zainteresowani komunikatami CBC, które zostały uzupełnione o przypełnienie ISO 10126, gdy komunikat ma dobrze znaną lub przewidywalną strukturę stopek.</span><span class="sxs-lookup"><span data-stu-id="7d17d-151">Research has led Microsoft to be further concerned about CBC messages that are padded with ISO 10126-equivalent padding when the message has a well-known or predictable footer structure.</span></span> <span data-ttu-id="7d17d-152">Na przykład zawartość przygotowana zgodnie z regułami składni szyfrowania XML i zalecenia dotyczące przetwarzania (xmlenc, EncryptedXml).</span><span class="sxs-lookup"><span data-stu-id="7d17d-152">For example, content prepared under the rules of the W3C XML Encryption Syntax and Processing Recommendation (xmlenc, EncryptedXml).</span></span> <span data-ttu-id="7d17d-153">Chociaż wskazówki dotyczące W3C podpisywania wiadomości są uważane za odpowiednie, firma Microsoft zaleca, aby zawsze przeprowadzać szyfrowanie i podpisywanie.</span><span class="sxs-lookup"><span data-stu-id="7d17d-153">While the W3C guidance to sign the message then encrypt was considered appropriate at the time, Microsoft now recommends always doing encrypt-then-sign.</span></span>

<span data-ttu-id="7d17d-154">Deweloperzy aplikacji powinni zawsze mieć pewność, że sprawdzają możliwość zastosowania klucza podpisu asymetrycznego, ponieważ nie istnieje relacja zaufania między kluczem asymetrycznym a dowolnym komunikatem.</span><span class="sxs-lookup"><span data-stu-id="7d17d-154">Application developers should always be mindful of verifying the applicability of an asymmetric signature key, as there's no inherent trust relationship between an asymmetric key and an arbitrary message.</span></span>

## <a name="details"></a><span data-ttu-id="7d17d-155">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="7d17d-155">Details</span></span>

<span data-ttu-id="7d17d-156">W przeszłości nastąpiło jednomyślne zaszyfrowanie i uwierzytelnienie ważnych danych przy użyciu takich metod jak HMAC lub sygnatury RSA.</span><span class="sxs-lookup"><span data-stu-id="7d17d-156">Historically, there has been consensus that it's important to both encrypt and authenticate important data, using means such as HMAC or RSA signatures.</span></span> <span data-ttu-id="7d17d-157">Istnieje jednak mniej jasne wskazówki dotyczące sekwencji operacji szyfrowania i uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7d17d-157">However, there has been less clear guidance as to how to sequence the encryption and authentication operations.</span></span> <span data-ttu-id="7d17d-158">Ze względu na lukę w zabezpieczeniach w tym artykule wskazówki firmy Microsoft mają teraz zawsze używać odmian "Szyfruj-and-Sign".</span><span class="sxs-lookup"><span data-stu-id="7d17d-158">Due to the vulnerability detailed in this article, Microsoft's guidance is now to always use the "encrypt-then-sign" paradigm.</span></span> <span data-ttu-id="7d17d-159">Oznacza to, że najpierw szyfruje dane przy użyciu klucza symetrycznego, a następnie oblicza sygnaturę adresu MAC lub asymetrycznego w postaci tekstu szyfrowanego (dane zaszyfrowane).</span><span class="sxs-lookup"><span data-stu-id="7d17d-159">That is, first encrypt data using a symmetric key, then compute a MAC or asymmetric signature over the ciphertext (encrypted data).</span></span> <span data-ttu-id="7d17d-160">Podczas odszyfrowywania danych wykonaj odwracanie.</span><span class="sxs-lookup"><span data-stu-id="7d17d-160">When decrypting data, perform the reverse.</span></span> <span data-ttu-id="7d17d-161">Najpierw Potwierdź adres MAC lub podpis tekstu szyfrowanego, a następnie Odszyfruj go.</span><span class="sxs-lookup"><span data-stu-id="7d17d-161">First, confirm the MAC or signature of the ciphertext, then decrypt it.</span></span>

<span data-ttu-id="7d17d-162">Wiadomo, że klasa luk w zabezpieczeniach, znana jako "dopełnienie ataków Oracle", już istnieje przez ponad 10 lat.</span><span class="sxs-lookup"><span data-stu-id="7d17d-162">A class of vulnerabilities known as "padding oracle attacks" have been known to exist for over 10 years.</span></span> <span data-ttu-id="7d17d-163">Luki w zabezpieczeniach umożliwiają atakującemu odszyfrowanie danych szyfrowanych przez algorytmy bloku symetrycznego, takie jak AES i 3DES, przy użyciu nie więcej niż 4096 prób na blok danych.</span><span class="sxs-lookup"><span data-stu-id="7d17d-163">These vulnerabilities allow an attacker to decrypt data encrypted by symmetric block algorithms, such as AES and 3DES, using no more than 4096 attempts per block of data.</span></span> <span data-ttu-id="7d17d-164">Te luki w zabezpieczeniach korzystają z faktu, że Szyfry blokowe są najczęściej używane z możliwymi do zweryfikowania danymi na końcu.</span><span class="sxs-lookup"><span data-stu-id="7d17d-164">These vulnerabilities make use of the fact that block ciphers are most frequently used with verifiable padding data at the end.</span></span> <span data-ttu-id="7d17d-165">Okazało się, że jeśli osoba atakująca może zmodyfikować szyfrowanie i dowiedzieć się, czy manipulowanie powodowało błąd w formacie uzupełnienia na końcu, osoba atakująca może odszyfrować dane.</span><span class="sxs-lookup"><span data-stu-id="7d17d-165">It was found that if an attacker can tamper with ciphertext and find out whether the tampering caused an error in the format of the padding at the end, the attacker can decrypt the data.</span></span>

<span data-ttu-id="7d17d-166">Początkowo praktyczne ataki dotyczyły usług, które zwracają różne kody błędów w oparciu o to, czy dopełnienie było prawidłowe, takie jak [ASP.NET luk w](/security-updates/SecurityBulletins/2010/ms10-070)zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="7d17d-166">Initially, practical attacks were based on services that would return different error codes based on whether padding was valid, such as the ASP.NET vulnerability [MS10-070](/security-updates/SecurityBulletins/2010/ms10-070).</span></span> <span data-ttu-id="7d17d-167">Jednak firma Microsoft uważa, że jest to praktyczne, aby przeprowadzić podobne ataki, używając tylko różnic czasu między przetwarzaniem prawidłowym i nieprawidłowym uzupełnieniem.</span><span class="sxs-lookup"><span data-stu-id="7d17d-167">However, Microsoft now believes that it's practical to conduct similar attacks using only the differences in timing between processing valid and invalid padding.</span></span>

<span data-ttu-id="7d17d-168">Pod warunkiem, że schemat szyfrowania używa podpisu i że weryfikacja podpisu jest wykonywana ze stałym środowiskiem uruchomieniowym dla danej długości danych (niezależnie od zawartości), integralność danych można zweryfikować bez emitowania jakichkolwiek informacji do osoby atakującej za pośrednictwem [kanału bocznego](https://en.wikipedia.org/wiki/Side-channel_attack).</span><span class="sxs-lookup"><span data-stu-id="7d17d-168">Provided that the encryption scheme employs a signature and that the signature verification is performed with a fixed runtime for a given length of data (irrespective of the contents), the data integrity can be verified without emitting any information to an attacker via a [side channel](https://en.wikipedia.org/wiki/Side-channel_attack).</span></span> <span data-ttu-id="7d17d-169">Ze względu na to, że sprawdzanie integralności odrzuci wszystkie naruszone komunikaty, dopełnienie zagrożeń firmy Oracle zostało skorygowane.</span><span class="sxs-lookup"><span data-stu-id="7d17d-169">Since the integrity check rejects any tampered messages, the padding oracle threat is mitigated.</span></span>

## <a name="guidance"></a><span data-ttu-id="7d17d-170">Wskazówki</span><span class="sxs-lookup"><span data-stu-id="7d17d-170">Guidance</span></span>

<span data-ttu-id="7d17d-171">Przede wszystkim firma Microsoft zaleca, aby wszystkie dane, które mają wymagania dotyczące poufności, były przesyłane za pośrednictwem Transport Layer Security (TLS), następnika SSL (SSL).</span><span class="sxs-lookup"><span data-stu-id="7d17d-171">First and foremost, Microsoft recommends that any data that has confidentiality needs be transmitted over Transport Layer Security (TLS), the successor to Secure Sockets Layer (SSL).</span></span>

<span data-ttu-id="7d17d-172">Następnie Przeanalizuj swoją aplikację w:</span><span class="sxs-lookup"><span data-stu-id="7d17d-172">Next, analyze your application to:</span></span>

- <span data-ttu-id="7d17d-173">Zapoznaj się z precyzyjnymi informacjami o debugowanym szyfrowaniu oraz o tym, jakie szyfrowanie jest zapewniane przez używane platformy i interfejsy API.</span><span class="sxs-lookup"><span data-stu-id="7d17d-173">Understand precisely what encryption you're performing and what encryption is being provided by the platforms and APIs you're using.</span></span>
- <span data-ttu-id="7d17d-174">Należy upewnić się, że każde użycie w każdej warstwie [algorytmu symetrycznego szyfrowania bloku](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), takie jak AES i 3DES, w trybie CBC obejmuje użycie kontroli integralności danych z tajnym kluczem (w postaci nieasymetrycznego, algorytmu HMAC lub zmiany trybu szyfrowania na [uwierzytelnianie uwierzytelnione](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE), np. GCM lub CCM).</span><span class="sxs-lookup"><span data-stu-id="7d17d-174">Be certain that each usage at each layer of a symmetric [block cipher algorithm](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), such as AES and 3DES, in CBC mode incorporate the use of a secret-keyed data integrity check (an asymmetric signature, an HMAC, or to change the cipher mode to an [authenticated encryption](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE) mode such as GCM or CCM).</span></span>

<span data-ttu-id="7d17d-175">W oparciu o bieżące badania ogólnie uważa się, że po wykonaniu czynności związanych z uwierzytelnianiem i szyfrowaniem niezależnie od trybu nieae, uwierzytelnianie tekstu szyfrowanego (szyfrowania i podpisywania) jest najlepszą opcją ogólną.</span><span class="sxs-lookup"><span data-stu-id="7d17d-175">Based on the current research, it's generally believed that when the authentication and encryption steps are performed independently for non-AE modes of encryption, authenticating the ciphertext (encrypt-then-sign) is the best general option.</span></span> <span data-ttu-id="7d17d-176">Nie ma jednak żadnej prawidłowej odpowiedzi na kryptografię, a to uogólnienie nie jest tak dobre jak ukierunkowane porady z cryptographer Professional.</span><span class="sxs-lookup"><span data-stu-id="7d17d-176">However, there's no one-size-fits-all correct answer to cryptography and this generalization isn't as good as directed advice from a professional cryptographer.</span></span>

<span data-ttu-id="7d17d-177">Aplikacje, które nie mogą zmienić formatu komunikatów, ale mogą wykonać nieuwierzytelnione odszyfrowywanie CBC, aby próbować uwzględnić środki zaradcze, takie jak:</span><span class="sxs-lookup"><span data-stu-id="7d17d-177">Applications that are unable to change their messaging format but perform unauthenticated CBC decryption are encouraged to try to incorporate mitigations such as:</span></span>

- <span data-ttu-id="7d17d-178">Odszyfruj bez zezwalania na odszyfrowanie, aby zweryfikować lub usunąć uzupełnienie:</span><span class="sxs-lookup"><span data-stu-id="7d17d-178">Decrypt without allowing the decryptor to verify or remove padding:</span></span>
  - <span data-ttu-id="7d17d-179">Wszelkie uzupełnienia, które zostały zastosowane nadal muszą zostać usunięte lub zignorowane, przenosisz obciążenie do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7d17d-179">Any padding that was applied still needs to be removed or ignored, you're moving the burden into your application.</span></span>
  - <span data-ttu-id="7d17d-180">Korzyść polega na tym, że weryfikacja uzupełniania i usunięcie może być włączone do innej logiki weryfikacji danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7d17d-180">The benefit is that the padding verification and removal can be incorporated into other application data verification logic.</span></span> <span data-ttu-id="7d17d-181">Jeśli weryfikacja uzupełniania i weryfikacja danych można wykonać w stałym czasie, zagrożenie zostanie zmniejszone.</span><span class="sxs-lookup"><span data-stu-id="7d17d-181">If the padding verification and data verification can be done in constant time, the threat is reduced.</span></span>
  - <span data-ttu-id="7d17d-182">Ponieważ interpretacja uzupełniania zmienia długość komunikatu, nadal mogą być emitowane informacje o chronometrażu.</span><span class="sxs-lookup"><span data-stu-id="7d17d-182">Since the interpretation of the padding changes the perceived message length, there may still be timing information emitted from this approach.</span></span>
- <span data-ttu-id="7d17d-183">Zmień tryb uzupełniania odszyfrowywania na ISO10126:</span><span class="sxs-lookup"><span data-stu-id="7d17d-183">Change the decryption padding mode to ISO10126:</span></span>
  - <span data-ttu-id="7d17d-184">Uzupełnienie odszyfrowywania ISO10126 jest zgodne z uzupełnieniem szyfrowania i ANSIX923 szyfrowaniem.</span><span class="sxs-lookup"><span data-stu-id="7d17d-184">ISO10126 decryption padding is compatible with both PKCS7 encryption padding and ANSIX923 encryption padding.</span></span>
  - <span data-ttu-id="7d17d-185">Zmiana trybu zmniejsza uzupełnianie wiedzy Oracle do 1 bajt zamiast całego bloku.</span><span class="sxs-lookup"><span data-stu-id="7d17d-185">Changing the mode reduces the padding oracle knowledge to 1 byte instead of the entire block.</span></span> <span data-ttu-id="7d17d-186">Jeśli jednak zawartość ma dobrze znaną stopkę, taką jak zamykający element XML, powiązane ataki mogą nadal zaatakować resztę wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7d17d-186">However, if the content has a well-known footer, such as a closing XML element, related attacks can continue to attack the rest of the message.</span></span>
  - <span data-ttu-id="7d17d-187">Uniemożliwia to również odzyskiwanie zwykłego tekstu w sytuacjach, gdy atakujący może przekształcić ten sam tekst w taki sposób, aby był szyfrowany wielokrotnie przy użyciu innego przesunięcia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="7d17d-187">This also doesn't prevent plaintext recovery in situations where the attacker can coerce the same plaintext to be encrypted multiple times with a different message offset.</span></span>
- <span data-ttu-id="7d17d-188">Ocenianie wywołania odszyfrowania w celu przeprowadzenia rozgłaszania sygnału czasu:</span><span class="sxs-lookup"><span data-stu-id="7d17d-188">Gate the evaluation of a decryption call to dampen the timing signal:</span></span>
  - <span data-ttu-id="7d17d-189">Obliczenie czasu wstrzymania musi mieć wartość minimalną przekraczającą maksymalną ilość czasu, jaką może wykonać operacja odszyfrowywania dla dowolnego segmentu danych zawierającego uzupełnienie.</span><span class="sxs-lookup"><span data-stu-id="7d17d-189">The computation of hold time must have a minimum in excess of the maximum amount of time the decryption operation would take for any data segment that contains padding.</span></span>
  - <span data-ttu-id="7d17d-190">Obliczenia czasu powinny odbywać się zgodnie ze wskazówkami dotyczącymi [uzyskiwania sygnatur czasowych o wysokiej rozdzielczości](/windows/desktop/sysinfo/acquiring-high-resolution-time-stamps), a nie za pomocą <xref:System.Environment.TickCount?displayProperty=nameWithType> (podlegają przewróceniu/przepełnieniu) lub odejmowania dwóch sygnatur czasowych systemu (z zastrzeżeniem błędów dopasowania NTP).</span><span class="sxs-lookup"><span data-stu-id="7d17d-190">Time computations should be done according to the guidance in [Acquiring high-resolution time stamps](/windows/desktop/sysinfo/acquiring-high-resolution-time-stamps), not by using <xref:System.Environment.TickCount?displayProperty=nameWithType> (subject to roll-over/overflow) or subtracting two system timestamps (subject to NTP adjustment errors).</span></span>
  - <span data-ttu-id="7d17d-191">Obliczenia czasu muszą uwzględniać operacje odszyfrowywania, w tym wszystkie potencjalne wyjątki w zarządzanych lub aplikacjach C++ , a nie tylko na końcu.</span><span class="sxs-lookup"><span data-stu-id="7d17d-191">Time computations must be inclusive of the decryption operation including all potential exceptions in managed or C++ applications, not just padded onto the end.</span></span>
  - <span data-ttu-id="7d17d-192">Jeśli jeszcze nie określono sukcesu lub niepowodzenia, Brama czasu musi zwrócić błąd po wygaśnięciu.</span><span class="sxs-lookup"><span data-stu-id="7d17d-192">If success or failure has been determined yet, the timing gate needs to return failure when it expires.</span></span>
- <span data-ttu-id="7d17d-193">Usługi, które wykonują nieuwierzytelnione odszyfrowywanie, powinny mieć monitorowanie w celu wykrycia, że pozostała część komunikatów "nieprawidłowe" została przeprowadzona.</span><span class="sxs-lookup"><span data-stu-id="7d17d-193">Services that are performing unauthenticated decryption should have monitoring in place to detect that a flood of "invalid" messages has come through.</span></span>
  - <span data-ttu-id="7d17d-194">Należy pamiętać, że ten sygnał obejmuje zarówno fałszywie dodatnie (dane uszkodzone), jak i fałszywe negatywne (rozproszenie ataku w wystarczająco długim czasie w celu uniknięcia wykrywania).</span><span class="sxs-lookup"><span data-stu-id="7d17d-194">Bear in mind that this signal carries both false positives (legitimately corrupted data) and false negatives (spreading out the attack over a sufficiently long time to evade detection).</span></span>

## <a name="finding-vulnerable-code---native-applications"></a><span data-ttu-id="7d17d-195">Znajdowanie zagrożonych aplikacji natywnych kodu</span><span class="sxs-lookup"><span data-stu-id="7d17d-195">Finding vulnerable code - native applications</span></span>

<span data-ttu-id="7d17d-196">W przypadku programów utworzonych w oparciu o bibliotekę kryptografii systemu Windows: nowej generacji (CNG):</span><span class="sxs-lookup"><span data-stu-id="7d17d-196">For programs built against the Windows Cryptography: Next Generation (CNG) library:</span></span>

- <span data-ttu-id="7d17d-197">Wywołanie odszyfrowywania to [BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt), określając flagę `BCRYPT_BLOCK_PADDING`.</span><span class="sxs-lookup"><span data-stu-id="7d17d-197">The decryption call is to [BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt), specifying the `BCRYPT_BLOCK_PADDING` flag.</span></span>
- <span data-ttu-id="7d17d-198">Obsługa klucza została zainicjowana przez wywołanie [BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty) z ustawionym na `BCRYPT_CHAIN_MODE_CBC`[BCRYPT_CHAINING_MODE](/windows/desktop/SecCNG/cng-property-identifiers#BCRYPT_CHAINING_MODE) .</span><span class="sxs-lookup"><span data-stu-id="7d17d-198">The key handle has been initialized by calling [BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty) with [BCRYPT_CHAINING_MODE](/windows/desktop/SecCNG/cng-property-identifiers#BCRYPT_CHAINING_MODE) set to `BCRYPT_CHAIN_MODE_CBC`.</span></span>
  - <span data-ttu-id="7d17d-199">Ponieważ `BCRYPT_CHAIN_MODE_CBC` jest wartością domyślną, kod, którego to dotyczy, może nie mieć przypisanej żadnej wartości dla `BCRYPT_CHAINING_MODE`.</span><span class="sxs-lookup"><span data-stu-id="7d17d-199">Since `BCRYPT_CHAIN_MODE_CBC` is the default, affected code may not have assigned any value for `BCRYPT_CHAINING_MODE`.</span></span>

<span data-ttu-id="7d17d-200">W przypadku programów utworzonych przy użyciu starszego interfejsu API usług kryptograficznych systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="7d17d-200">For programs built against the older Windows Cryptographic API:</span></span>

- <span data-ttu-id="7d17d-201">Wywołanie odszyfrowujący jest [CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) z `Final=TRUE`.</span><span class="sxs-lookup"><span data-stu-id="7d17d-201">The decryption call is to [CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) with `Final=TRUE`.</span></span>
- <span data-ttu-id="7d17d-202">Obsługa klucza została zainicjowana przez wywołanie [CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam) z ustawionym na `CRYPT_MODE_CBC`[KP_MODE](/windows/desktop/api/wincrypt/nf-wincrypt-cryptgetkeyparam) .</span><span class="sxs-lookup"><span data-stu-id="7d17d-202">The key handle has been initialized by calling [CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam) with [KP_MODE](/windows/desktop/api/wincrypt/nf-wincrypt-cryptgetkeyparam) set to `CRYPT_MODE_CBC`.</span></span>
  - <span data-ttu-id="7d17d-203">Ponieważ `CRYPT_MODE_CBC` jest wartością domyślną, kod, którego to dotyczy, może nie mieć przypisanej żadnej wartości dla `KP_MODE`.</span><span class="sxs-lookup"><span data-stu-id="7d17d-203">Since `CRYPT_MODE_CBC` is the default, affected code may not have assigned any value for `KP_MODE`.</span></span>

## <a name="finding-vulnerable-code---managed-applications"></a><span data-ttu-id="7d17d-204">Znajdowanie zagrożonych aplikacji zarządzanych przez kod</span><span class="sxs-lookup"><span data-stu-id="7d17d-204">Finding vulnerable code - managed applications</span></span>

- <span data-ttu-id="7d17d-205">Wywołanie odszyfrowywania to metody <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> lub <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> w <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7d17d-205">The decryption call is to the <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> or <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> methods on <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="7d17d-206">Obejmuje to następujące typy pochodne w ramach platformy .NET, ale mogą również zawierać typy innych firm:</span><span class="sxs-lookup"><span data-stu-id="7d17d-206">This includes the following derived types within the .NET, but may also include third-party types:</span></span>
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
- <span data-ttu-id="7d17d-207">Właściwość <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> została ustawiona na <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>lub <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7d17d-207">The <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> property was set to <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>, or <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="7d17d-208">Ponieważ <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> jest wartością domyślną, kod, którego to dotyczy, może nigdy nie mieć przypisanej właściwości <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7d17d-208">Since <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> is the default, affected code may never have assigned the <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> property.</span></span>
- <span data-ttu-id="7d17d-209">Właściwość <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> została ustawiona na <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7d17d-209">The <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> property was set to <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType></span></span>
  - <span data-ttu-id="7d17d-210">Ponieważ <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> jest wartością domyślną, kod, którego to dotyczy, może nigdy nie mieć przypisanej właściwości <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7d17d-210">Since <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> is the default, affected code may never have assigned the <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> property.</span></span>

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a><span data-ttu-id="7d17d-211">Znajdowanie niezagrożonego kodu — składnia komunikatu kryptograficznego</span><span class="sxs-lookup"><span data-stu-id="7d17d-211">Finding vulnerable code - cryptographic message syntax</span></span>

<span data-ttu-id="7d17d-212">Nieuwierzytelniony komunikat CMS EnvelopedData, którego zaszyfrowana zawartość używa trybu CBC AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) lub RC2 (1.2.840.113549.3.2) podatne na ataki, a także komunikaty używające innych algorytmów szyfrowania bloku w trybie CBC.</span><span class="sxs-lookup"><span data-stu-id="7d17d-212">An unauthenticated CMS EnvelopedData message whose encrypted content uses the CBC mode of AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) or RC2 (1.2.840.113549.3.2) is vulnerable, as well as messages using any other block cipher algorithms in CBC mode.</span></span>

<span data-ttu-id="7d17d-213">Chociaż szyfry strumienia nie są podatne na tę konkretną lukę w zabezpieczeniach, firma Microsoft zaleca zawsze uwierzytelnianie danych przez sprawdzenie wartości ContentEncryptionAlgorithm.</span><span class="sxs-lookup"><span data-stu-id="7d17d-213">While stream ciphers aren't susceptible to this particular vulnerability, Microsoft recommends always authenticating the data over inspecting the ContentEncryptionAlgorithm value.</span></span>

<span data-ttu-id="7d17d-214">W przypadku zarządzanych aplikacji obiekt BLOB EnvelopedData CMS może zostać wykryty jako dowolna wartość, która jest przenoszona do <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="7d17d-214">For managed applications, a CMS EnvelopedData blob can be detected as any value that is passed to <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.</span></span>

<span data-ttu-id="7d17d-215">W przypadku aplikacji natywnych można wykryć obiekt BLOB EnvelopedData CMS jako dowolną wartość dostarczoną do uchwytu CMS za pośrednictwem [CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) , którego [CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam) wynikiem jest `CMSG_ENVELOPED` i/lub dojście usługi CMS jest później wysyłane instrukcją `CMSG_CTRL_DECRYPT` za pośrednictwem [CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol).</span><span class="sxs-lookup"><span data-stu-id="7d17d-215">For native applications, a CMS EnvelopedData blob can be detected as any value provided to a CMS handle via [CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) whose resulting [CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam) is `CMSG_ENVELOPED` and/or the CMS handle is later sent a `CMSG_CTRL_DECRYPT` instruction via [CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol).</span></span>

## <a name="vulnerable-code-example---managed"></a><span data-ttu-id="7d17d-216">Przykład kodu zagrożonego</span><span class="sxs-lookup"><span data-stu-id="7d17d-216">Vulnerable code example - managed</span></span>

<span data-ttu-id="7d17d-217">Ta metoda odczytuje plik cookie i odszyfrowuje go i nie jest widoczne sprawdzanie integralności danych.</span><span class="sxs-lookup"><span data-stu-id="7d17d-217">This method reads a cookie and decrypts it and no data integrity check is visible.</span></span> <span data-ttu-id="7d17d-218">W związku z tym zawartość pliku cookie odczytywanego przez tę metodę może być zaatakowana przez użytkownika, który go otrzymał lub przez osobę atakującą, która uzyskała zaszyfrowaną wartość cookie.</span><span class="sxs-lookup"><span data-stu-id="7d17d-218">Therefore, the contents of a cookie that is read by this method can be attacked by the user who received it, or by any attacker who has obtained the encrypted cookie value.</span></span>

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

## <a name="example-code-following-recommended-practices---managed"></a><span data-ttu-id="7d17d-219">Przykładowy kod zgodnie z zalecanymi praktykami — zarządzany</span><span class="sxs-lookup"><span data-stu-id="7d17d-219">Example code following recommended practices - managed</span></span>

<span data-ttu-id="7d17d-220">Następujący przykładowy kod używa niestandardowego formatu komunikatów</span><span class="sxs-lookup"><span data-stu-id="7d17d-220">The following sample code uses a non-standard message format of</span></span>

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

<span data-ttu-id="7d17d-221">w przypadku, gdy identyfikatory algorytmów `cipher_algorithm_id` i `hmac_algorithm_id` są reprezentacją aplikacji lokalnych (niestandardowych) tych algorytmów.</span><span class="sxs-lookup"><span data-stu-id="7d17d-221">where the `cipher_algorithm_id` and `hmac_algorithm_id` algorithm identifiers are application-local (non-standard) representations of those algorithms.</span></span> <span data-ttu-id="7d17d-222">Identyfikatory te mogą mieć sens w innych częściach istniejącego protokołu obsługi komunikatów, a nie jako elementu ByteStream połączone.</span><span class="sxs-lookup"><span data-stu-id="7d17d-222">These identifiers may make sense in other parts of your existing messaging protocol instead of as a bare concatenated bytestream.</span></span>

<span data-ttu-id="7d17d-223">Ten przykład używa również jednego klucza głównego, aby utworzyć zarówno klucz szyfrowania, jak i klucz HMAC.</span><span class="sxs-lookup"><span data-stu-id="7d17d-223">This example also uses a single master key to derive both an encryption key and an HMAC key.</span></span> <span data-ttu-id="7d17d-224">Jest to wygodne dla wygody do wyłączania aplikacji z pojedynczą aplikacją do aplikacji z podwójnym podwyższeniem poziomu i zapewnienia, że te dwa klucze są różne.</span><span class="sxs-lookup"><span data-stu-id="7d17d-224">This is provided both as a convenience for turning a singly-keyed application into a dual-keyed application, and to encourage keeping the two keys as different values.</span></span> <span data-ttu-id="7d17d-225">Zapewnia to dalsze gwarancję, że klucz HMAC i klucz szyfrowania nie mogą zostać zsynchronizowane.</span><span class="sxs-lookup"><span data-stu-id="7d17d-225">It further guarantees that the HMAC key and encryption key can't get out of synchronization.</span></span>

<span data-ttu-id="7d17d-226">Ten przykład nie akceptuje <xref:System.IO.Stream> szyfrowania ani odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="7d17d-226">This sample doesn't accept a <xref:System.IO.Stream> for either encryption or decryption.</span></span> <span data-ttu-id="7d17d-227">Bieżący format danych sprawia, że szyfrowanie jednokrotne jest trudne, ponieważ wartość `hmac_tag` poprzedza tekst szyfrowany.</span><span class="sxs-lookup"><span data-stu-id="7d17d-227">The current data format makes one-pass encrypt difficult because the `hmac_tag` value precedes the ciphertext.</span></span> <span data-ttu-id="7d17d-228">Jednak ten format został wybrany, ponieważ zachowuje wszystkie elementy o stałym rozmiarze na początku, aby ułatwić dalsze zachowanie analizatora.</span><span class="sxs-lookup"><span data-stu-id="7d17d-228">However, this format was chosen because it keeps all of the fixed-size elements at the beginning to keep the parser simpler.</span></span> <span data-ttu-id="7d17d-229">Przy użyciu tego formatu danych możliwe jest odszyfrowanie jednokrotne, ale w celu zaimplementowania GetHashAndReset i sprawdzenia wyniku przed wywołaniem TransformFinalBlock należy zachować ostrożność.</span><span class="sxs-lookup"><span data-stu-id="7d17d-229">With this data format, one-pass decrypt is possible, though an implementer is cautioned to call GetHashAndReset and verify the result before calling TransformFinalBlock.</span></span> <span data-ttu-id="7d17d-230">Jeśli szyfrowanie strumieniowe jest ważne, może być wymagany inny tryb AE.</span><span class="sxs-lookup"><span data-stu-id="7d17d-230">If streaming encryption is important, then a different AE mode may be required.</span></span>

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
