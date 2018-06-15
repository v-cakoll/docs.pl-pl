---
title: Luki w zabezpieczeniach chronometrażu z trybie CBC odszyfrowywania symetrycznego za pomocą wypełnienia
description: Dowiedz się, jak wykrywanie i usuwanie luk w zabezpieczeniach chronometrażu z odszyfrowanie symetryczne tryb Cipher-Block Chaining (CBC) za pomocą wypełnienia.
ms.date: 06/12/2018
author: blowdart
ms.author: mairaw
ms.openlocfilehash: a07acbb943c430f6e26bec44f55a5c84306da513
ms.sourcegitcommit: 73a662360bbe2f43c19aca1fbcc2565025c60cd8
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2018
ms.locfileid: "35327270"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a><span data-ttu-id="9a3af-103">Luki w zabezpieczeniach chronometrażu z trybie CBC odszyfrowywania symetrycznego za pomocą wypełnienia</span><span class="sxs-lookup"><span data-stu-id="9a3af-103">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>

<span data-ttu-id="9a3af-104">Microsoft, w obecnie znane badaniach kryptograficznych, w oparciu uznaje, z wyjątkiem sytuacji bardzo specyficznego nie jest już bezpieczne odszyfrowanie danych zaszyfrowanych z trybem Cipher-Block Chaining (CBC) szyfrowania symetrycznego, gdy dopełnienie podlegające weryfikacji zastosowane bez pierwszy zapewniania integralności tekstu szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="9a3af-104">Microsoft, based on currently known cryptographic research, believes that, except for very specific circumstances, it's no longer safe to decrypt data encrypted with the Cipher-Block-Chaining (CBC) mode of symmetric encryption when verifiable padding has been applied without first ensuring the integrity of the ciphertext.</span></span>

## <a name="introduction"></a><span data-ttu-id="9a3af-105">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="9a3af-105">Introduction</span></span>

<span data-ttu-id="9a3af-106">Atak oracle uzupełnienie jest typem ataku przeciwko zaszyfrowanych danych, który umożliwia osobie atakującej na odszyfrowywanie zawartości danych, bez uprzedniego uzyskania informacji o kluczu.</span><span class="sxs-lookup"><span data-stu-id="9a3af-106">A padding oracle attack is a type of attack against encrypted data that allows the attacker to decrypt the contents of the data, without knowing the key.</span></span>

<span data-ttu-id="9a3af-107">Oracle odnosi się do "Powiadom" które daje atakująca informacje są one wykonywania akcji jest prawidłowa lub nie.</span><span class="sxs-lookup"><span data-stu-id="9a3af-107">An oracle refers to a "tell" which gives an attacker information about whether the action they're executing is correct or not.</span></span> <span data-ttu-id="9a3af-108">Wyobraź sobie odtwarzanie tablicę lub kart gry z elementem podrzędnym.</span><span class="sxs-lookup"><span data-stu-id="9a3af-108">Imagine playing a board or card game with a child.</span></span> <span data-ttu-id="9a3af-109">Po jej krój podświetlony z dużą uśmiech ponieważ Agnieszka przebywa o dokonanie dobry ruch, który jest oracle.</span><span class="sxs-lookup"><span data-stu-id="9a3af-109">When her face lights up with a big smile because she thinks she's about to make a good move, that's an oracle.</span></span> <span data-ttu-id="9a3af-110">Jako przeciwnika, można to oracle odpowiednio zaplanować przejście dalej.</span><span class="sxs-lookup"><span data-stu-id="9a3af-110">You, as the opponent, can use this oracle to plan your next move appropriately.</span></span>

<span data-ttu-id="9a3af-111">Uzupełnienie jest kryptograficznych określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="9a3af-111">Padding is a specific cryptographic term.</span></span> <span data-ttu-id="9a3af-112">Niektóre szyfrów, które są algorytmy używane do szyfrowania danych, działają na bloki danych, gdzie każdy blok jest o stałym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="9a3af-112">Some ciphers, which are the algorithms used to encrypt your data, work on blocks of data where each block is a fixed size.</span></span> <span data-ttu-id="9a3af-113">Jeśli dane, które chcesz zaszyfrować nie ma właściwego rozmiaru w celu wypełnienia bloki, danych jest wypełniane, dopóki nie robi.</span><span class="sxs-lookup"><span data-stu-id="9a3af-113">If the data you want to encrypt isn't the right size to fill the blocks, your data is padded until it does.</span></span> <span data-ttu-id="9a3af-114">Wiele form uzupełnienia wymagają tego uzupełnienia zawsze być obecne, nawet jeśli oryginalny wprowadzono właściwego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="9a3af-114">Many forms of padding require that padding to always be present, even if the original input was of the right size.</span></span> <span data-ttu-id="9a3af-115">Dzięki temu uzupełnienia zawsze można bezpiecznie usunąć po odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="9a3af-115">This allows the padding to always be safely removed upon decryption.</span></span>

<span data-ttu-id="9a3af-116">Zestawienie dwie rzeczy, wdrożenia oprogramowania z oracle dopełnienie wykazuje, czy odszyfrowane dane mają prawidłowy dopełnienie.</span><span class="sxs-lookup"><span data-stu-id="9a3af-116">Putting the two things together, a software implementation with a padding oracle reveals whether decrypted data has valid padding.</span></span> <span data-ttu-id="9a3af-117">Programu oracle można coś najprostszą zwracanie wartości informacją "Nieprawidłowy dopełnienie" lub coś bardziej skomplikowany, takich jak widoczny różnych czasu przetwarzania prawidłowy blok przeciwieństwie nieprawidłowy blok.</span><span class="sxs-lookup"><span data-stu-id="9a3af-117">The oracle could be something as simple as returning a value that says "Invalid padding" or something more complicated like taking a measurably different time to process a valid block as opposed to an invalid block.</span></span>

<span data-ttu-id="9a3af-118">Szyfry opartej na blokach ma inna właściwość o nazwie tryb, który określa relacji danych w pierwszym bloku danych w drugim bloku, i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="9a3af-118">Block-based ciphers have another property, called the mode, which determines the relationship of data in the first block to the data in the second block, and so on.</span></span> <span data-ttu-id="9a3af-119">Jeden z trybów najczęściej używane jest CBC.</span><span class="sxs-lookup"><span data-stu-id="9a3af-119">One of the most commonly used modes is CBC.</span></span> <span data-ttu-id="9a3af-120">CBC wprowadza początkowej blok losowych, znane jako inicjowania wektora (IV) i łączy poprzedniego bloku z wynikiem statycznych szyfrowania, aby była w taki sposób, że szyfrowanie ten sam komunikat z tym samym kluczem zawsze nie tworzy tych samych zaszyfrowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="9a3af-120">CBC introduces an initial random block, known as the Initialization Vector (IV), and combines the previous block with the result of static encryption to make it such that encrypting the same message with the same key doesn't always produce the same encrypted output.</span></span>

<span data-ttu-id="9a3af-121">Osobie atakującej wykorzystanie programu oracle dopełnienie, w połączeniu z struktury danych CBC, do wysyłania wiadomości nieco zmienione do kodu, który ujawnia programu oracle i zachować wysyłanie danych do czasu programu oracle dowie się, dane są poprawne.</span><span class="sxs-lookup"><span data-stu-id="9a3af-121">An attacker can use a padding oracle, in combination with how CBC data is structured, to send slightly changed messages to the code that exposes the oracle, and keep sending data until the oracle tells them the data is correct.</span></span> <span data-ttu-id="9a3af-122">Osoba atakująca może odszyfrować wiadomości po bicie, z tej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="9a3af-122">From this response, the attacker can decrypt the message byte by byte.</span></span>

<span data-ttu-id="9a3af-123">Nowoczesne komputera sieci są takie wysokiej jakości, że osoba atakująca może wykryć bardzo małe (mniej niż 0,1 ms) różnice w wykonywania czasu w systemach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="9a3af-123">Modern computer networks are of such high quality that an attacker can detect very small (less than 0.1 ms) differences in execution time on remote systems.</span></span> <span data-ttu-id="9a3af-124">Aplikacje, które są przy założeniu, że pomyślnie odszyfrowywania tylko zdarzyć, gdy dane nie został zmieniony przez niepowołane może być narażony na ataki z narzędzia, które są przeznaczone do przestrzegania różnice w odszyfrowywania zakończone powodzeniem i niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="9a3af-124">Applications that are assuming that a successful decryption can only happen when the data wasn't tampered with may be vulnerable to attack from tools that are designed to observe differences in successful and unsuccessful decryption.</span></span> <span data-ttu-id="9a3af-125">Ta różnica czasu może być bardziej znaczących w niektórych językach lub biblioteki niż inne, teraz uważa się, że jest to praktyczne zagrożenie dla wszystkich języków i bibliotek, gdy aplikacji odpowiedzi na błędy jest brana pod uwagę.</span><span class="sxs-lookup"><span data-stu-id="9a3af-125">While this timing difference may be more significant in some languages or libraries than others, it's now believed that this is a practical threat for all languages and libraries when the application's response to failure is taken into account.</span></span>

<span data-ttu-id="9a3af-126">Atak polega na możliwość zmieniania zaszyfrowanych danych i testowania wynik z programu oracle.</span><span class="sxs-lookup"><span data-stu-id="9a3af-126">This attack relies on the ability to change the encrypted data and test the result with the oracle.</span></span> <span data-ttu-id="9a3af-127">Jedynym sposobem, aby ograniczyć pełni ataku jest wykrywa zmiany do zaszyfrowanych danych i odmówić wykonywać w niej żadnych akcji.</span><span class="sxs-lookup"><span data-stu-id="9a3af-127">The only way to fully mitigate the attack is to detect changes to the encrypted data and refuse to perform any actions on it.</span></span> <span data-ttu-id="9a3af-128">Standardowy sposób, w tym celu jest utworzenie podpisu dla danych i sprawdź poprawność tego podpisu, przed wykonaniem jakichkolwiek operacji.</span><span class="sxs-lookup"><span data-stu-id="9a3af-128">The standard way to do this is to create a signature for the data and validate that signature before any operations are performed.</span></span> <span data-ttu-id="9a3af-129">Podpis musi być możliwe do zweryfikowania, nie można utworzyć przez osobę atakującą, w przeciwnym razie ich czy zmienić zaszyfrowane dane, a następnie obliczyć podpisu nowy, oparty na zmienione dane.</span><span class="sxs-lookup"><span data-stu-id="9a3af-129">The signature must be verifiable, it cannot be created by the attacker, otherwise they'd change the encrypted data, then compute a new signature based on the changed data.</span></span> <span data-ttu-id="9a3af-130">Jeden typ wspólnego z odpowiednim podpisem nosi nazwę kod uwierzytelniania wiadomości z kluczem skrótu (HMAC).</span><span class="sxs-lookup"><span data-stu-id="9a3af-130">One common type of appropriate signature is known as a keyed-hash message authentication code (HMAC).</span></span> <span data-ttu-id="9a3af-131">HMAC różni się od sumy kontrolnej, że trwa klucz tajny, znane tylko osoby HMAC generująca lub osoby jej skuteczność.</span><span class="sxs-lookup"><span data-stu-id="9a3af-131">An HMAC differs from a checksum in that it takes a secret key, known only to the person producing the HMAC and to the person validating it.</span></span> <span data-ttu-id="9a3af-132">Bez posiadaniu klucza nie można utworzyć poprawne HMAC.</span><span class="sxs-lookup"><span data-stu-id="9a3af-132">Without possession of the key, you can't produce a correct HMAC.</span></span> <span data-ttu-id="9a3af-133">Podczas odbierania danych, należy wykonać zaszyfrowane dane, niezależnie obliczeniowe HMAC przy użyciu klucza tajnego, możesz i nadawcy udziału, a następnie porównaj HMAC one wysyłane za jedną należy obliczyć.</span><span class="sxs-lookup"><span data-stu-id="9a3af-133">When you receive your data, you'd take the encrypted data, independently compute the HMAC using the secret key you and the sender share, then compare the HMAC they sent against the one you computed.</span></span> <span data-ttu-id="9a3af-134">To porównanie musi być stałą czasu, w przeciwnym razie dodaniu innego oracle wykrywalny, co pozwala na inny rodzaj ataku.</span><span class="sxs-lookup"><span data-stu-id="9a3af-134">This comparison must be constant time, otherwise you've added another detectable oracle, allowing a different type of attack.</span></span>

<span data-ttu-id="9a3af-135">Podsumowując do używania dopełniane szyfrów bloku CBC bezpiecznie, należy połączyć je z HMAC (lub innego sprawdzania integralności danych), który weryfikacji przy użyciu porównanie stałej czasu przed przystąpieniem do odszyfrowania danych.</span><span class="sxs-lookup"><span data-stu-id="9a3af-135">In summary, to use padded CBC block ciphers safely, you must combine them with an HMAC (or another data integrity check) that you validate using a constant time comparison before trying to decrypt the data.</span></span> <span data-ttu-id="9a3af-136">Ponieważ wszystkie komunikaty zmieniony zająć jednocześnie Kwota do tworzenia odpowiedzi, nie będzie mógł ataku.</span><span class="sxs-lookup"><span data-stu-id="9a3af-136">Since all altered messages take the same amount time to produce a response, the attack is prevented.</span></span>

## <a name="who-is-vulnerable"></a><span data-ttu-id="9a3af-137">Kto jest zagrożony</span><span class="sxs-lookup"><span data-stu-id="9a3af-137">Who is vulnerable</span></span>

<span data-ttu-id="9a3af-138">Ta luka w zabezpieczeniach dotyczy zarządzane i natywne aplikacje, które wykonują własne szyfrowanie i odszyfrowywanie.</span><span class="sxs-lookup"><span data-stu-id="9a3af-138">This vulnerability applies to both managed and native applications that are performing their own encryption and decryption.</span></span> <span data-ttu-id="9a3af-139">Obejmuje to, na przykład:</span><span class="sxs-lookup"><span data-stu-id="9a3af-139">This includes, for example:</span></span>

- <span data-ttu-id="9a3af-140">Aplikacja, która powoduje zaszyfrowanie pliku cookie do nowszej odszyfrowywania na serwerze.</span><span class="sxs-lookup"><span data-stu-id="9a3af-140">An application that encrypts a cookie for later decryption on the server.</span></span>
- <span data-ttu-id="9a3af-141">Aplikacja bazy danych, która zapewnia możliwość przez użytkowników do wstawiania danych do tabeli, w których kolumny są później odszyfrować.</span><span class="sxs-lookup"><span data-stu-id="9a3af-141">A database application that provides the ability for users to insert data into a table whose columns are later decrypted.</span></span>
- <span data-ttu-id="9a3af-142">Aplikacja transferu danych, która korzysta z szyfrowania do ochrony danych podczas przesyłania przy użyciu klucza wspólnego.</span><span class="sxs-lookup"><span data-stu-id="9a3af-142">A data transfer application that relies on encryption using a shared key to protect the data in transit.</span></span>
- <span data-ttu-id="9a3af-143">Aplikacja, która szyfruje i odszyfrowuje wiadomości "od wewnątrz" tunelu TLS.</span><span class="sxs-lookup"><span data-stu-id="9a3af-143">An application that encrypts and decrypts messages "inside" the TLS tunnel.</span></span>

<span data-ttu-id="9a3af-144">Należy pamiętać, że używają wyłącznie protokołu TLS może nie chronią w tych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="9a3af-144">Note that using TLS alone may not protect you in these scenarios.</span></span>

<span data-ttu-id="9a3af-145">Usterce aplikacji:</span><span class="sxs-lookup"><span data-stu-id="9a3af-145">A vulnerable application:</span></span>

- <span data-ttu-id="9a3af-146">Odszyfrowuje dane w trybie CBC szyfrowania z trybem dopełnienie podlegające weryfikacji, takie jak PKCS #7 lub ANSI X.923.</span><span class="sxs-lookup"><span data-stu-id="9a3af-146">Decrypts data using the CBC cipher mode with a verifiable padding mode, such as PKCS#7 or ANSI X.923.</span></span>
- <span data-ttu-id="9a3af-147">Wykonuje odszyfrowywanie bez o wykonywane sprawdzanie integralności (za pośrednictwem MAC lub asymetrycznego podpisu cyfrowego).</span><span class="sxs-lookup"><span data-stu-id="9a3af-147">Performs the decryption without having performed a data integrity check (via a MAC or an asymmetric digital signature).</span></span>

<span data-ttu-id="9a3af-148">Dotyczy to również aplikacje, rozszerzający abstrakcje w górnej części tych podstawowych, takich jak struktury EnvelopedData składni wiadomości kryptograficznych (PKCS #7/CMS).</span><span class="sxs-lookup"><span data-stu-id="9a3af-148">This also applies to applications built on top of abstractions over top of these primitives, such as the Cryptographic Message Syntax (PKCS#7/CMS) EnvelopedData structure.</span></span>

## <a name="related-areas-of-concern"></a><span data-ttu-id="9a3af-149">Powiązane obszary zainteresowania</span><span class="sxs-lookup"><span data-stu-id="9a3af-149">Related areas of concern</span></span>

<span data-ttu-id="9a3af-150">Badania spowodowało Microsoft w celu dalszego zajmującym CBC wiadomości, które są dopełniane przy ISO 10126-równoważne wypełnienia podczas wiadomości ma strukturę stopki dobrze znanego lub prognozowanych.</span><span class="sxs-lookup"><span data-stu-id="9a3af-150">Research has led Microsoft to be further concerned about CBC messages that are padded with ISO 10126-equivalent padding when the message has a well-known or predictable footer structure.</span></span> <span data-ttu-id="9a3af-151">Na przykład zawartość przygotowany zgodnie z regułami W3C XML szyfrowania składni i przetwarzania zalecenie (xmlenc EncryptedXml).</span><span class="sxs-lookup"><span data-stu-id="9a3af-151">For example, content prepared under the rules of the W3C XML Encryption Syntax and Processing Recommendation (xmlenc, EncryptedXml).</span></span> <span data-ttu-id="9a3af-152">Gdy wskazówki W3C do podpisania wiadomości, a następnie szyfrować uznano za właściwe, w tym czasie, firma Microsoft zaleca teraz zawsze podczas szyfrowania to znak.</span><span class="sxs-lookup"><span data-stu-id="9a3af-152">While the W3C guidance to sign the message then encrypt was considered appropriate at the time, Microsoft now recommends always doing encrypt-then-sign.</span></span>

<span data-ttu-id="9a3af-153">Deweloperzy aplikacji powinien zawsze mieć sprawdzanie możliwości zastosowania danego klucza asymetrycznego podpisu, mając na uwadze, ponieważ nie ma żadnych relacji zaufania związane między klucza asymetrycznego i dowolnego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="9a3af-153">Application developers should always be mindful of verifying the applicability of an asymmetric signature key, as there's no inherent trust relationship between an asymmetric key and an arbitrary message.</span></span>

## <a name="details"></a><span data-ttu-id="9a3af-154">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="9a3af-154">Details</span></span>

<span data-ttu-id="9a3af-155">W przeszłości ma zostać konsensu, które są ważne do szyfrowania i uwierzytelniania ważnych danych, przy użyciu środków, takich jak HMAC lub RSA podpisów.</span><span class="sxs-lookup"><span data-stu-id="9a3af-155">Historically, there has been consensus that it's important to both encrypt and authenticate important data, using means such as HMAC or RSA signatures.</span></span> <span data-ttu-id="9a3af-156">Jednak było w niej mniej wyraźnych wskazówek sposobów sekwencji operacji szyfrowania i uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="9a3af-156">However, there has been less clear guidance as to how to sequence the encryption and authentication operations.</span></span> <span data-ttu-id="9a3af-157">Z powodu usterki szczegółowo opisane w tym artykule wskazówkami firmy Microsoft jest teraz zawsze używaj modelu "szyfrowania następnie znaku".</span><span class="sxs-lookup"><span data-stu-id="9a3af-157">Due to the vulnerability detailed in this article, Microsoft's guidance is now to always use the "encrypt-then-sign" paradigm.</span></span> <span data-ttu-id="9a3af-158">Oznacza to najpierw szyfrowania danych przy użyciu klucza symetrycznego, a następnie obliczeniowego MAC lub podpisu asymetrycznego za pośrednictwem tekstu szyfrowanego (zaszyfrowanych danych).</span><span class="sxs-lookup"><span data-stu-id="9a3af-158">That is, first encrypt data using a symmetric key, then compute a MAC or asymmetric signature over the ciphertext (encrypted data).</span></span> <span data-ttu-id="9a3af-159">Podczas deszyfrowania danych, należy przeprowadzić odwrotnej.</span><span class="sxs-lookup"><span data-stu-id="9a3af-159">When decrypting data, perform the reverse.</span></span> <span data-ttu-id="9a3af-160">Najpierw upewnij się, MAC lub podpis tekstu szyfrowanego, a następnie go odszyfrować.</span><span class="sxs-lookup"><span data-stu-id="9a3af-160">First, confirm the MAC or signature of the ciphertext, then decrypt it.</span></span>

<span data-ttu-id="9a3af-161">Klasa jest ogólnie znana jako "padding ataków oracle" znane istnieje ponad 10 lat luk w zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="9a3af-161">A class of vulnerabilities known as "padding oracle attacks" have been known to exist for over 10 years.</span></span> <span data-ttu-id="9a3af-162">Te luki w zabezpieczeniach osoba atakująca na odszyfrowanie danych zaszyfrowanych przez blok symetryczne algorytmy, takie jak AES i 3DES, przy użyciu nie więcej niż 4096 prób na blok danych.</span><span class="sxs-lookup"><span data-stu-id="9a3af-162">These vulnerabilities allow an attacker to decrypt data encrypted by symmetric block algorithms, such as AES and 3DES, using no more than 4096 attempts per block of data.</span></span> <span data-ttu-id="9a3af-163">Wprowadź te luki w zabezpieczeniach korzystanie z faktu, że zablokowanie szyfrów najczęściej używanych z danymi weryfikowalny dopełnienie na końcu.</span><span class="sxs-lookup"><span data-stu-id="9a3af-163">These vulnerabilities make use of the fact that block ciphers are most frequently used with verifiable padding data at the end.</span></span> <span data-ttu-id="9a3af-164">Okazało się, że jeśli osoba atakująca może manipulować tekstu szyfrowanego i sprawdzić, czy o naruszeniu spowodował błąd w formacie wypełnienia na końcu, osoba atakująca może odszyfrować danych.</span><span class="sxs-lookup"><span data-stu-id="9a3af-164">It was found that if an attacker can tamper with ciphertext and find out whether the tampering caused an error in the format of the padding at the end, the attacker can decrypt the data.</span></span>

<span data-ttu-id="9a3af-165">Początkowo praktyczne ataków znajdowały się na usługami zwracającymi kody błędów różnych oparte na czy dopełnienie była prawidłowa, taka jak luki w zabezpieczeniach ASP.NET [MS10-070](https://technet.microsoft.com/library/security/ms10-070.aspx).</span><span class="sxs-lookup"><span data-stu-id="9a3af-165">Initially, practical attacks were based on services that would return different error codes based on whether padding was valid, such as the ASP.NET vulnerability [MS10-070](https://technet.microsoft.com/library/security/ms10-070.aspx).</span></span> <span data-ttu-id="9a3af-166">Jednak firma Microsoft teraz uzna, że jest to możliwe przeprowadzenie podobne ataki za pomocą tylko różnice czasu między przetwarzania dopełnienie prawidłowe oraz nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="9a3af-166">However, Microsoft now believes that it's practical to conduct similar attacks using only the differences in timing between processing valid and invalid padding.</span></span>

<span data-ttu-id="9a3af-167">Pod warunkiem, że podpis wykorzystuje schemat szyfrowania i weryfikacja podpisu jest wykonywane z stałym środowiska uruchomieniowego dla podanej długości danych (niezależnie od zawartości), bez emitowanie informacji, które można sprawdzić spójność danych Osoba atakująca za pośrednictwem [kanału po stronie](https://en.wikipedia.org/wiki/Side-channel_attack).</span><span class="sxs-lookup"><span data-stu-id="9a3af-167">Provided that the encryption scheme employs a signature and that the signature verification is performed with a fixed runtime for a given length of data (irrespective of the contents), the data integrity can be verified without emitting any information to an attacker via a [side channel](https://en.wikipedia.org/wiki/Side-channel_attack).</span></span> <span data-ttu-id="9a3af-168">Ponieważ sprawdzania integralności odrzuca komunikaty zmodyfikowany, skuteczność została osłabiona zagrożeń oracle dopełnienia.</span><span class="sxs-lookup"><span data-stu-id="9a3af-168">Since the integrity check rejects any tampered messages, the padding oracle threat is mitigated.</span></span>

## <a name="guidance"></a><span data-ttu-id="9a3af-169">Wskazówki</span><span class="sxs-lookup"><span data-stu-id="9a3af-169">Guidance</span></span>

<span data-ttu-id="9a3af-170">Najpierw i, firma Microsoft zaleca musi być przekazywane za pośrednictwem zabezpieczeń TLS (Transport Layer), następnika do Secure Sockets Layer (SSL) zawierający poufności danych.</span><span class="sxs-lookup"><span data-stu-id="9a3af-170">First and foremost, Microsoft recommends that any data that has confidentiality needs be transmitted over Transport Layer Security (TLS), the successor to Secure Sockets Layer (SSL).</span></span>

<span data-ttu-id="9a3af-171">Następnie analizować aplikacji:</span><span class="sxs-lookup"><span data-stu-id="9a3af-171">Next, analyze your application to:</span></span>

- <span data-ttu-id="9a3af-172">Dowiedz się dokładnie szyfrowania, jaką wykonujesz i jakie szyfrowanie jest świadczona przez platform i interfejsów API używasz.</span><span class="sxs-lookup"><span data-stu-id="9a3af-172">Understand precisely what encryption you're performing and what encryption is being provided by the platforms and APIs you're using.</span></span>
- <span data-ttu-id="9a3af-173">Się upewnić, że każdy użycia w każdej warstwie symetrycznego [algorytmu szyfrowania bloku](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), takie jak AES i 3DES w trybie CBC zawierają stosowania sprawdzania integralności danych klucze tajne (podpisu asymetrycznego HMAC lub zmienić tryb szyfrowania do [uwierzytelniony szyfrowania](https://en.wikipedia.org/wiki/Authenticated_encryption) trybu (AE), takim jak GCM lub CCM).</span><span class="sxs-lookup"><span data-stu-id="9a3af-173">Be certain that each usage at each layer of a symmetric [block cipher algorithm](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), such as AES and 3DES, in CBC mode incorporate the use of a secret-keyed data integrity check (an asymmetric signature, an HMAC, or to change the cipher mode to an [authenticated encryption](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE) mode such as GCM or CCM).</span></span>

<span data-ttu-id="9a3af-174">W oparciu o bieżący badań, ogólnie uważa się, że w przypadku uwierzytelnianie i szyfrowanie kroki są wykonywane niezależnie dla trybów AE bez szyfrowania, uwierzytelniania szyfrowanego (szyfrowanie następnie Podpisz) jest najlepszą opcją ogólne.</span><span class="sxs-lookup"><span data-stu-id="9a3af-174">Based on the current research, it's generally believed that when the authentication and encryption steps are performed independently for non-AE modes of encryption, authenticating the ciphertext (encrypt-then-sign) is the best general option.</span></span> <span data-ttu-id="9a3af-175">Niestety nie są bez pasującego poprawną odpowiedź na kryptografii i jak ukierunkowanej poradę professional cryptographer nie jest to generalizacji.</span><span class="sxs-lookup"><span data-stu-id="9a3af-175">However, there's no one-size-fits-all correct answer to cryptography and this generalization isn't as good as directed advice from a professional cryptographer.</span></span>

<span data-ttu-id="9a3af-176">Aplikacje, które można zmienić ich format wiadomości, jednak wykonywać nieuwierzytelnione odszyfrowywania CBC zaleca się spróbuj zastosować środki zaradcze, takich jak:</span><span class="sxs-lookup"><span data-stu-id="9a3af-176">Applications that are unable to change their messaging format but perform unauthenticated CBC decryption are encouraged to try to incorporate mitigations such as:</span></span>

- <span data-ttu-id="9a3af-177">Odszyfrowywania bez możliwości odszyfrowujący weryfikacji lub usunąć uzupełnienie:</span><span class="sxs-lookup"><span data-stu-id="9a3af-177">Decrypt without allowing the decryptor to verify or remove padding:</span></span>
  - <span data-ttu-id="9a3af-178">Wszelkie uzupełnienia, która została zastosowana nadal musi zostać usunięte lub zignorowane, przenoszenia obciążeń w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9a3af-178">Any padding that was applied still needs to be removed or ignored, you're moving the burden into your application.</span></span>
  - <span data-ttu-id="9a3af-179">Korzyścią jest to, że dopełnienie weryfikacji i usuwania mogą być włączone w innych logikę weryfikacji danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9a3af-179">The benefit is that the padding verification and removal can be incorporated into other application data verification logic.</span></span> <span data-ttu-id="9a3af-180">Dopełnienie weryfikacji i weryfikacja danych mogą być przeprowadzane w czasie stałej, ograniczono zagrożenia.</span><span class="sxs-lookup"><span data-stu-id="9a3af-180">If the padding verification and data verification can be done in constant time, the threat is reduced.</span></span>
  - <span data-ttu-id="9a3af-181">Ponieważ interpretacji wypełnienia zmienia długość komunikatu postrzegana, może nadal być informacji wyemitowanego z tej metody.</span><span class="sxs-lookup"><span data-stu-id="9a3af-181">Since the interpretation of the padding changes the perceived message length, there may still be timing information emitted from this approach.</span></span>
- <span data-ttu-id="9a3af-182">Zmień tryb uzupełniania odszyfrowywania ISO10126:</span><span class="sxs-lookup"><span data-stu-id="9a3af-182">Change the decryption padding mode to ISO10126:</span></span>
  - <span data-ttu-id="9a3af-183">Dopełnienie odszyfrowywania ISO10126 jest zgodny z zarówno wypełnienie PKCS7 i wypełnienie ANSIX923.</span><span class="sxs-lookup"><span data-stu-id="9a3af-183">ISO10126 decryption padding is compatible with both PKCS7 encryption padding and ANSIX923 encryption padding.</span></span>
  - <span data-ttu-id="9a3af-184">Zmienianie trybu ogranicza wiedzy oracle uzupełnienie do 1 bajt zamiast całego bloku.</span><span class="sxs-lookup"><span data-stu-id="9a3af-184">Changing the mode reduces the padding oracle knowledge to 1 byte instead of the entire block.</span></span> <span data-ttu-id="9a3af-185">Jeśli zawartość ma dobrze znanego stopki, takich jak zamykającego elementu XML pokrewne ataków jednak na ataki pozostałej części wiadomości.</span><span class="sxs-lookup"><span data-stu-id="9a3af-185">However, if the content has a well-known footer, such as a closing XML element, related attacks can continue to attack the rest of the message.</span></span>
  - <span data-ttu-id="9a3af-186">To również nie uniemożliwia odzyskiwanie zwykłego tekstu w sytuacji, gdy osoba atakująca można przekształcić tego samego zwykły tekst do zaszyfrowania wiele razy z przesunięciem inny komunikat.</span><span class="sxs-lookup"><span data-stu-id="9a3af-186">This also doesn't prevent plaintext recovery in situations where the attacker can coerce the same plaintext to be encrypted multiple times with a different message offset.</span></span>
- <span data-ttu-id="9a3af-187">Brama obliczania wywołania odszyfrowywania Rozmoczenie sygnału czasu:</span><span class="sxs-lookup"><span data-stu-id="9a3af-187">Gate the evaluation of a decryption call to dampen the timing signal:</span></span>
  - <span data-ttu-id="9a3af-188">Obliczenia czasu blokady musi mieć co najmniej przekracza maksymalną ilość czasu, który wykonać operacji odszyfrowywania dla żadnego z segmentów danych zawierający dopełnienia.</span><span class="sxs-lookup"><span data-stu-id="9a3af-188">The computation of hold time must have a minimum in excess of the maximum amount of time the decryption operation would take for any data segment that contains padding.</span></span>
  - <span data-ttu-id="9a3af-189">Obliczenia czas należy przeprowadzić zgodnie z instrukcjami podanymi w [pobierania sygnatur czasowych wysokiej rozdzielczości](https://msdn.microsoft.com/library/windows/desktop/dn55340.aspx), nie za pomocą <xref:System.Environment.TickCount?displayProperty=nameWithType> (może ulec roll-over/przepełnienie) lub usunięcie dwóch systemu sygnatur czasowych (zgodnie z korekty NTP błędy).</span><span class="sxs-lookup"><span data-stu-id="9a3af-189">Time computations should be done according to the guidance in [Acquiring high-resolution time stamps](https://msdn.microsoft.com/library/windows/desktop/dn55340.aspx), not by using <xref:System.Environment.TickCount?displayProperty=nameWithType> (subject to roll-over/overflow) or subtracting two system timestamps (subject to NTP adjustment errors).</span></span>
  - <span data-ttu-id="9a3af-190">Obliczenia czas musi być tym operacji odszyfrowywania wszystkich potencjalnych wyjątków w tym zarządzane lub aplikacje w języku C++ nie tylko. dopełniane na końcu.</span><span class="sxs-lookup"><span data-stu-id="9a3af-190">Time computations must be inclusive of the decryption operation including all potential exceptions in managed or C++ applications, not just padded onto the end.</span></span>
  - <span data-ttu-id="9a3af-191">Jeśli powodzenie lub niepowodzenie odnalezieniu jeszcze bramy chronometrażu musi zwracać błąd, po jego wygaśnięciu.</span><span class="sxs-lookup"><span data-stu-id="9a3af-191">If success or failure has been determined yet, the timing gate needs to return failure when it expires.</span></span>
- <span data-ttu-id="9a3af-192">Usługi, które działają nieuwierzytelnione odszyfrowywania powinien mieć monitorowania w celu wykrycia, czy powódź "nieprawidłowe" komunikatów do trybu za pośrednictwem.</span><span class="sxs-lookup"><span data-stu-id="9a3af-192">Services that are performing unauthenticated decryption should have monitoring in place to detect that a flood of "invalid" messages has come through.</span></span>
  - <span data-ttu-id="9a3af-193">Przy tym pamiętać, że ten sygnał prowadzi zarówno fałszywych alarmów (legalnie uszkodzone dane), jak i fałszywych wyników negatywnych (rozkładanie ataków za pośrednictwem wystarczająco dużo czasu uniknięcia wykrywania).</span><span class="sxs-lookup"><span data-stu-id="9a3af-193">Bear in mind that this signal carries both false positives (legitimately corrupted data) and false negatives (spreading out the attack over a sufficiently long time to evade detection).</span></span>

## <a name="finding-vulnerable-code---native-applications"></a><span data-ttu-id="9a3af-194">Wyszukiwanie kodu luki w zabezpieczeniach - natywnych aplikacji</span><span class="sxs-lookup"><span data-stu-id="9a3af-194">Finding vulnerable code - native applications</span></span>

<span data-ttu-id="9a3af-195">Dla programów, które utworzono przy użyciu kryptografii systemu Windows: Biblioteka nowej generacji (CNG):</span><span class="sxs-lookup"><span data-stu-id="9a3af-195">For programs built against the Windows Cryptography: Next Generation (CNG) library:</span></span>

- <span data-ttu-id="9a3af-196">Wywołanie odszyfrowywania ma na celu [BCryptDecrypt](https://msdn.microsoft.com/library/windows/desktop/aa375391.aspx), określania `BCRYPT_BLOCK_PADDING` flagi.</span><span class="sxs-lookup"><span data-stu-id="9a3af-196">The decryption call is to [BCryptDecrypt](https://msdn.microsoft.com/library/windows/desktop/aa375391.aspx), specifying the `BCRYPT_BLOCK_PADDING` flag.</span></span>
- <span data-ttu-id="9a3af-197">Dojście klucza została zainicjowana przez wywołanie metody [BCryptSetProperty](https://msdn.microsoft.com/library/windows/desktop/aa375504.aspx) z [BCRYPT_CHAINING_MODE](https://msdn.microsoft.com/library/windows/desktop/aa376211.aspx#BCRYPT_CHAINING_MODE) ustawioną `BCRYPT_CHAIN_MODE_CBC`.</span><span class="sxs-lookup"><span data-stu-id="9a3af-197">The key handle has been initialized by calling [BCryptSetProperty](https://msdn.microsoft.com/library/windows/desktop/aa375504.aspx) with [BCRYPT_CHAINING_MODE](https://msdn.microsoft.com/library/windows/desktop/aa376211.aspx#BCRYPT_CHAINING_MODE) set to `BCRYPT_CHAIN_MODE_CBC`.</span></span>
  - <span data-ttu-id="9a3af-198">Ponieważ `BCRYPT_CHAIN_MODE_CBC` jest ustawienie domyślne, których to dotyczy kodu nie może przypisać wszystkie wartości `BCRYPT_CHAINING_MODE`.</span><span class="sxs-lookup"><span data-stu-id="9a3af-198">Since `BCRYPT_CHAIN_MODE_CBC` is the default, affected code may not have assigned any value for `BCRYPT_CHAINING_MODE`.</span></span>

<span data-ttu-id="9a3af-199">Dla programów utworzono przy użyciu starszej kryptograficznego interfejsu API systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="9a3af-199">For programs built against the older Windows Cryptographic API:</span></span>

- <span data-ttu-id="9a3af-200">Wywołanie odszyfrowywania ma na celu [CryptDecrypt](https://msdn.microsoft.com/library/windows/desktop/aa379913.aspx) z `Final=TRUE`.</span><span class="sxs-lookup"><span data-stu-id="9a3af-200">The decryption call is to [CryptDecrypt](https://msdn.microsoft.com/library/windows/desktop/aa379913.aspx) with `Final=TRUE`.</span></span>
- <span data-ttu-id="9a3af-201">Dojście klucza została zainicjowana przez wywołanie metody [CryptSetKeyParam](https://msdn.microsoft.com/library/windows/desktop/aa380272.aspx) z [KP_MODE](https://msdn.microsoft.com/library/windows/desktop/aa379949.aspx#KP_MODE) ustawioną `CRYPT_MODE_CBC`.</span><span class="sxs-lookup"><span data-stu-id="9a3af-201">The key handle has been initialized by calling [CryptSetKeyParam](https://msdn.microsoft.com/library/windows/desktop/aa380272.aspx) with [KP_MODE](https://msdn.microsoft.com/library/windows/desktop/aa379949.aspx#KP_MODE) set to `CRYPT_MODE_CBC`.</span></span>
  - <span data-ttu-id="9a3af-202">Ponieważ `CRYPT_MODE_CBC` jest ustawienie domyślne, których to dotyczy kodu nie może przypisać wszystkie wartości `KP_MODE`.</span><span class="sxs-lookup"><span data-stu-id="9a3af-202">Since `CRYPT_MODE_CBC` is the default, affected code may not have assigned any value for `KP_MODE`.</span></span>

## <a name="finding-vulnerable-code---managed-applications"></a><span data-ttu-id="9a3af-203">Znajdowanie niebezpieczny kod - zarządzanych aplikacji</span><span class="sxs-lookup"><span data-stu-id="9a3af-203">Finding vulnerable code - managed applications</span></span>

- <span data-ttu-id="9a3af-204">Wywołanie odszyfrowywania ma na celu <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> lub <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> metody <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9a3af-204">The decryption call is to the <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> or <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> methods on <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="9a3af-205">Dostępne są następujące typy pochodne w ramach programu .NET, ale mogą również obejmować typów innych firm:</span><span class="sxs-lookup"><span data-stu-id="9a3af-205">This includes the following derived types within the .NET, but may also include third-party types:</span></span>
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
- <span data-ttu-id="9a3af-206"><xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> Ustawiono właściwość <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>, lub <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9a3af-206">The <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> property was set to <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>, or <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="9a3af-207">Ponieważ <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> jest ustawienie domyślne, których to dotyczy kodu może nigdy nie przypisano <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="9a3af-207">Since <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> is the default, affected code may never have assigned the <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> property.</span></span>
- <span data-ttu-id="9a3af-208"><xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> Ustawiono właściwość <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9a3af-208">The <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> property was set to <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType></span></span>
  - <span data-ttu-id="9a3af-209">Ponieważ <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> jest ustawienie domyślne, których to dotyczy kodu może nigdy nie przypisano <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="9a3af-209">Since <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> is the default, affected code may never have assigned the <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> property.</span></span>

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a><span data-ttu-id="9a3af-210">Wyszukiwanie kodu luki w zabezpieczeniach - składni wiadomości kryptograficznych</span><span class="sxs-lookup"><span data-stu-id="9a3af-210">Finding vulnerable code - cryptographic message syntax</span></span>

<span data-ttu-id="9a3af-211">Wiadomość CMS EnvelopedData nieuwierzytelnione którego zaszyfrowaną zawartość używa trybu CBC AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), (1.3.14.3.2.7) DES, 3DES (1.2.840.113549.3.7) lub RC2 (1.2.840.113549.3.2) jest narażony, jak również w wiadomości w trybie CBC przy użyciu innych algorytmów szyfrowania bloku.</span><span class="sxs-lookup"><span data-stu-id="9a3af-211">An unauthenticated CMS EnvelopedData message whose encrypted content uses the CBC mode of AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) or RC2 (1.2.840.113549.3.2) is vulnerable, as well as messages using any other block cipher algorithms in CBC mode.</span></span>

<span data-ttu-id="9a3af-212">Gdy szyfrów strumienia nie są podatne na tę lukę w zabezpieczeniach określonego, firma Microsoft zaleca zawsze uwierzytelnianie danych za pośrednictwem sprawdzania wartości ContentEncryptionAlgorithm.</span><span class="sxs-lookup"><span data-stu-id="9a3af-212">While stream ciphers aren't susceptible to this particular vulnerability, Microsoft recommends always authenticating the data over inspecting the ContentEncryptionAlgorithm value.</span></span>

<span data-ttu-id="9a3af-213">Dla zarządzanych aplikacji EnvelopedData CMS, obiektów blob może być wykryte jako żadnej wartości, który jest przekazywany do <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="9a3af-213">For managed applications, a CMS EnvelopedData blob can be detected as any value that is passed to <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.</span></span>

<span data-ttu-id="9a3af-214">Dla natywnych aplikacji mogą być wykrywane CMS EnvelopedData obiektu blob jako podanie do uchwytu CMS za pomocą dowolnej wartości [CryptMsgUpdate](https://msdn.microsoft.com/library/windows/desktop/aa380231.aspx) których wynikowa [CMSG_TYPE_PARAM](https://msdn.microsoft.com/library/windows/desktop/aa380227.aspx) jest `CMSG_ENVELOPED` i/lub dojście CMS później wysyłane `CMSG_CTRL_DECRYPT` instrukcji za pomocą [CryptMsgControl](https://msdn.microsoft.com/library/windows/desktop/aa380220.aspx).</span><span class="sxs-lookup"><span data-stu-id="9a3af-214">For native applications, a CMS EnvelopedData blob can be detected as any value provided to a CMS handle via [CryptMsgUpdate](https://msdn.microsoft.com/library/windows/desktop/aa380231.aspx) whose resulting [CMSG_TYPE_PARAM](https://msdn.microsoft.com/library/windows/desktop/aa380227.aspx) is `CMSG_ENVELOPED` and/or the CMS handle is later sent a `CMSG_CTRL_DECRYPT` instruction via [CryptMsgControl](https://msdn.microsoft.com/library/windows/desktop/aa380220.aspx).</span></span>

## <a name="vulnerable-code-example---managed"></a><span data-ttu-id="9a3af-215">Przykład kodu luki w zabezpieczeniach — zarządzane</span><span class="sxs-lookup"><span data-stu-id="9a3af-215">Vulnerable code example - managed</span></span>

<span data-ttu-id="9a3af-216">Ta metoda odczytuje plik cookie i odszyfrowuje ją i sprawdzanie integralności danych nie jest widoczny.</span><span class="sxs-lookup"><span data-stu-id="9a3af-216">This method reads a cookie and decrypts it and no data integrity check is visible.</span></span> <span data-ttu-id="9a3af-217">W związku z tym zawartość pliku cookie, który jest odczytywany przez tę metodę można ataku przez użytkownika, który otrzymał go, lub każda osoba atakująca, która uzyskała wartość zaszyfrowanego pliku cookie.</span><span class="sxs-lookup"><span data-stu-id="9a3af-217">Therefore, the contents of a cookie that is read by this method can be attacked by the user who received it, or by any attacker who has obtained the encrypted cookie value.</span></span>

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

## <a name="example-code-following-recommended-practices---managed"></a><span data-ttu-id="9a3af-218">Przykład kodu następujących zalecanych rozwiązań - zarządzany</span><span class="sxs-lookup"><span data-stu-id="9a3af-218">Example code following recommended practices - managed</span></span>

<span data-ttu-id="9a3af-219">Następujący przykładowy kod używa komunikatu niestandardowym formacie</span><span class="sxs-lookup"><span data-stu-id="9a3af-219">The following sample code uses a non-standard message format of</span></span>

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

<span data-ttu-id="9a3af-220">gdzie `cipher_algorithm_id` i `hmac_algorithm_id` algorytm identyfikatory są (niestandardowy) reprezentacje tych algorytmów lokalnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9a3af-220">where the `cipher_algorithm_id` and `hmac_algorithm_id` algorithm identifiers are application-local (non-standard) representations of those algorithms.</span></span> <span data-ttu-id="9a3af-221">Te identyfikatory może być uzasadniona w innych częściach z istniejącego protokołu obsługi zamiast jako systemu od zera połączonych strumienia bajtów.</span><span class="sxs-lookup"><span data-stu-id="9a3af-221">These identifiers may make sense in other parts of your existing messaging protocol instead of as a bare concatenated bytestream.</span></span>

<span data-ttu-id="9a3af-222">W tym przykładzie również korzysta z jednego klucza głównego pochodzić zarówno klucz szyfrowania, jak i klucz HMAC.</span><span class="sxs-lookup"><span data-stu-id="9a3af-222">This example also uses a single master key to derive both an encryption key and an HMAC key.</span></span> <span data-ttu-id="9a3af-223">To jest dostępna zarówno jako udogodnienie dla Włączanie aplikacji z kluczem pojedynczo do aplikacji z kluczem procesory i zachęca utrzymywanie dwa klucze, jak różne wartości.</span><span class="sxs-lookup"><span data-stu-id="9a3af-223">This is provided both as a convenience for turning a singly-keyed application into a dual-keyed application, and to encourage keeping the two keys as different values.</span></span> <span data-ttu-id="9a3af-224">Gwarantuje dalsze, nie można pobrać klucza HMAC i klucz szyfrowania poza synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="9a3af-224">It further guarantees that the HMAC key and encryption key can't get out of synchronization.</span></span>

<span data-ttu-id="9a3af-225">W tym przykładzie nie akceptuje <xref:System.IO.Stream> do szyfrowania lub odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="9a3af-225">This sample doesn't accept a <xref:System.IO.Stream> for either encryption or decryption.</span></span> <span data-ttu-id="9a3af-226">Bieżące dane formatu sprawia, że jeden przebieg szyfrowania trudne ponieważ `hmac_tag` wartość poprzedza tekstu szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="9a3af-226">The current data format makes one-pass encrypt difficult because the `hmac_tag` value precedes the ciphertext.</span></span> <span data-ttu-id="9a3af-227">Jednak ten format została wybrana, ponieważ utrzymuje wszystkich elementów o stałym rozmiarze na początku, aby zachować analizator prostsze.</span><span class="sxs-lookup"><span data-stu-id="9a3af-227">However, this format was chosen because it keeps all of the fixed-size elements at the beginning to keep the parser simpler.</span></span> <span data-ttu-id="9a3af-228">Z tego formatu danych odszyfrowywania jeden przebieg jest możliwe, że implementujący jest cautioned wywołać GetHashAndReset i sprawdź wynik przed wywołaniem metody TransformFinalBlock.</span><span class="sxs-lookup"><span data-stu-id="9a3af-228">With this data format, one-pass decrypt is possible, though an implementer is cautioned to call GetHashAndReset and verify the result before calling TransformFinalBlock.</span></span> <span data-ttu-id="9a3af-229">Jeśli szyfrowanie przesyłania strumieniowego odgrywa ważną rolę, inny tryb AE mogą być wymagane.</span><span class="sxs-lookup"><span data-stu-id="9a3af-229">If streaming encryption is important, then a different AE mode may be required.</span></span>

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
