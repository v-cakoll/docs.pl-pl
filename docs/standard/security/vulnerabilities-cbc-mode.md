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
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a><span data-ttu-id="60fce-103">Luki w zabezpieczeniach chronometrażu z odszyfrowywaniem symetrycznym w trybie CBC przy użyciu uzupełnienia</span><span class="sxs-lookup"><span data-stu-id="60fce-103">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>

<span data-ttu-id="60fce-104">Microsoft uważa, że nie jest już bezpieczne odszyfrowywanie danych zaszyfrowanych za pomocą trybu szyfrowania szyfrowania szyfrującego(CBC) szyfrowania symetrycznego, gdy zastosowano weryfikowalne dopełnienie bez uprzedniego zapewnienia integralności szyfru, z wyjątkiem bardzo specyficznych Okolicznościach.</span><span class="sxs-lookup"><span data-stu-id="60fce-104">Microsoft believes that it's no longer safe to decrypt data encrypted with the Cipher-Block-Chaining (CBC) mode of symmetric encryption when verifiable padding has been applied without first ensuring the integrity of the ciphertext, except for very specific circumstances.</span></span> <span data-ttu-id="60fce-105">Wyrok ten opiera się na obecnie znanych badaniach kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="60fce-105">This judgement is based on currently known cryptographic research.</span></span>

## <a name="introduction"></a><span data-ttu-id="60fce-106">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="60fce-106">Introduction</span></span>

<span data-ttu-id="60fce-107">Atak oracle dopełnienie jest rodzajem ataku na zaszyfrowane dane, który umożliwia osobie atakującej odszyfrowywanie zawartości danych, bez znajomości klucza.</span><span class="sxs-lookup"><span data-stu-id="60fce-107">A padding oracle attack is a type of attack against encrypted data that allows the attacker to decrypt the contents of the data, without knowing the key.</span></span>

<span data-ttu-id="60fce-108">Oracle odnosi się do "powiedz", który daje osobie atakującej informacje o tym, czy wykonywana akcja jest poprawna, czy nie.</span><span class="sxs-lookup"><span data-stu-id="60fce-108">An oracle refers to a "tell" which gives an attacker information about whether the action they're executing is correct or not.</span></span> <span data-ttu-id="60fce-109">Wyobraź sobie, że grasz z dzieckiem na planszy lub w grę karcianą.</span><span class="sxs-lookup"><span data-stu-id="60fce-109">Imagine playing a board or card game with a child.</span></span> <span data-ttu-id="60fce-110">Kiedy ich twarz zapala się z wielkim uśmiechem, ponieważ myślą, że mają zamiar zrobić dobry ruch, to wyrocznia.</span><span class="sxs-lookup"><span data-stu-id="60fce-110">When their face lights up with a big smile because they think they're about to make a good move, that's an oracle.</span></span> <span data-ttu-id="60fce-111">Ty, jako przeciwnik, możesz użyć tej wyroczni, aby odpowiednio zaplanować swój następny ruch.</span><span class="sxs-lookup"><span data-stu-id="60fce-111">You, as the opponent, can use this oracle to plan your next move appropriately.</span></span>

<span data-ttu-id="60fce-112">Dopełnienie to określony termin kryptograficzny.</span><span class="sxs-lookup"><span data-stu-id="60fce-112">Padding is a specific cryptographic term.</span></span> <span data-ttu-id="60fce-113">Niektóre szyfry, które są algorytmami używanymi do szyfrowania danych, działają na blokach danych, gdzie każdy blok ma stały rozmiar.</span><span class="sxs-lookup"><span data-stu-id="60fce-113">Some ciphers, which are the algorithms used to encrypt your data, work on blocks of data where each block is a fixed size.</span></span> <span data-ttu-id="60fce-114">Jeśli dane, które chcesz zaszyfrować, nie są odpowiednim rozmiarem do wypełnienia bloków, dane są wypełniane, dopóki tego nie zrobisz.</span><span class="sxs-lookup"><span data-stu-id="60fce-114">If the data you want to encrypt isn't the right size to fill the blocks, your data is padded until it does.</span></span> <span data-ttu-id="60fce-115">Wiele form dopełnienia wymagają, aby dopełnienie było zawsze obecne, nawet jeśli oryginalne dane wejściowe były o odpowiednim rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="60fce-115">Many forms of padding require that padding to always be present, even if the original input was of the right size.</span></span> <span data-ttu-id="60fce-116">Dzięki temu dopełnienie zawsze być bezpiecznie usunięte po odszyfrowywaniu.</span><span class="sxs-lookup"><span data-stu-id="60fce-116">This allows the padding to always be safely removed upon decryption.</span></span>

<span data-ttu-id="60fce-117">Łącząc te dwie rzeczy razem, implementacja oprogramowania z oracle dopełnienie ujawnia, czy odszyfrowane dane mają prawidłową dopełnienie.</span><span class="sxs-lookup"><span data-stu-id="60fce-117">Putting the two things together, a software implementation with a padding oracle reveals whether decrypted data has valid padding.</span></span> <span data-ttu-id="60fce-118">Oracle może być coś tak proste, jak zwracanie wartości, która mówi "Nieprawidłowe dopełnienie" lub coś bardziej skomplikowanego, jak biorąc wymiernie inny czas do przetworzenia prawidłowego bloku, w przeciwieństwie do nieprawidłowego bloku.</span><span class="sxs-lookup"><span data-stu-id="60fce-118">The oracle could be something as simple as returning a value that says "Invalid padding" or something more complicated like taking a measurably different time to process a valid block as opposed to an invalid block.</span></span>

<span data-ttu-id="60fce-119">Szyfry oparte na blokach mają inną właściwość, o nazwie tryb, która określa relację danych w pierwszym bloku do danych w drugim bloku i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="60fce-119">Block-based ciphers have another property, called the mode, which determines the relationship of data in the first block to the data in the second block, and so on.</span></span> <span data-ttu-id="60fce-120">Jednym z najczęściej używanych trybów jest CBC.</span><span class="sxs-lookup"><span data-stu-id="60fce-120">One of the most commonly used modes is CBC.</span></span> <span data-ttu-id="60fce-121">CBC wprowadza początkowy blok losowy, znany jako Wektor inicjowania (IV) i łączy poprzedni blok z wynikiem szyfrowania statycznego, aby uczynić go tak, że szyfrowanie tej samej wiadomości za pomocą tego samego klucza nie zawsze daje te same szyfrowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="60fce-121">CBC introduces an initial random block, known as the Initialization Vector (IV), and combines the previous block with the result of static encryption to make it such that encrypting the same message with the same key doesn't always produce the same encrypted output.</span></span>

<span data-ttu-id="60fce-122">Osoba atakująca może użyć oracle dopełnienia, w połączeniu z jak dane CBC jest zorganizowany, aby wysłać nieco zmienione wiadomości do kodu, który udostępnia oracle i zachować wysyłanie danych, dopóki oracle mówi im, że dane są poprawne.</span><span class="sxs-lookup"><span data-stu-id="60fce-122">An attacker can use a padding oracle, in combination with how CBC data is structured, to send slightly changed messages to the code that exposes the oracle, and keep sending data until the oracle tells them the data is correct.</span></span> <span data-ttu-id="60fce-123">Z tej odpowiedzi osoba atakująca może odszyfrować bajt wiadomości według bajtu.</span><span class="sxs-lookup"><span data-stu-id="60fce-123">From this response, the attacker can decrypt the message byte by byte.</span></span>

<span data-ttu-id="60fce-124">Nowoczesne sieci komputerowe są tak wysokiej jakości, że osoba atakująca może wykryć bardzo małe (mniej niż 0,1 ms) różnice w czasie wykonywania w systemach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="60fce-124">Modern computer networks are of such high quality that an attacker can detect very small (less than 0.1 ms) differences in execution time on remote systems.</span></span><span data-ttu-id="60fce-125">Aplikacje, które są przy założeniu, że pomyślne odszyfrowywanie może się zdarzyć tylko wtedy, gdy dane nie zostały naruszone, mogą być narażone na ataki z narzędzi, które są przeznaczone do obserwowania różnic w pomyślnym i nieudanym odszyfrowywaniu.</span><span class="sxs-lookup"><span data-stu-id="60fce-125"> Applications that are assuming that a successful decryption can only happen when the data wasn't tampered with may be vulnerable to attack from tools that are designed to observe differences in successful and unsuccessful decryption.</span></span> <span data-ttu-id="60fce-126">Chociaż ta różnica czasu może być bardziej istotne w niektórych językach lub bibliotekach niż inne, teraz uważa się, że jest to praktyczne zagrożenie dla wszystkich języków i bibliotek, gdy odpowiedź aplikacji na niepowodzenie jest brana pod uwagę.</span><span class="sxs-lookup"><span data-stu-id="60fce-126">While this timing difference may be more significant in some languages or libraries than others, it's now believed that this is a practical threat for all languages and libraries when the application's response to failure is taken into account.</span></span>

<span data-ttu-id="60fce-127">Ten atak opiera się na możliwości zmiany zaszyfrowanych danych i przetestowania wyniku za pomocą oracle.</span><span class="sxs-lookup"><span data-stu-id="60fce-127">This attack relies on the ability to change the encrypted data and test the result with the oracle.</span></span> <span data-ttu-id="60fce-128">Jedynym sposobem, aby w pełni złagodzić atak jest wykrycie zmian w zaszyfrowanych danych i odmówić wykonania jakichkolwiek działań na nim.</span><span class="sxs-lookup"><span data-stu-id="60fce-128">The only way to fully mitigate the attack is to detect changes to the encrypted data and refuse to perform any actions on it.</span></span> <span data-ttu-id="60fce-129">Standardowym sposobem, aby to zrobić jest utworzenie podpisu dla danych i sprawdzić poprawność tego podpisu przed wykonaniem jakichkolwiek operacji.</span><span class="sxs-lookup"><span data-stu-id="60fce-129">The standard way to do this is to create a signature for the data and validate that signature before any operations are performed.</span></span> <span data-ttu-id="60fce-130">Podpis musi być weryfikowalny, nie może zostać utworzony przez osobę atakującą, w przeciwnym razie zmieniłby zaszyfrowane dane, a następnie obliczyć nowy podpis na podstawie zmienionych danych.</span><span class="sxs-lookup"><span data-stu-id="60fce-130">The signature must be verifiable, it cannot be created by the attacker, otherwise they'd change the encrypted data, then compute a new signature based on the changed data.</span></span> <span data-ttu-id="60fce-131">Jeden typowy typ odpowiedniego podpisu jest znany jako kod uwierzytelniania komunikatów klucza mieszania (HMAC).</span><span class="sxs-lookup"><span data-stu-id="60fce-131">One common type of appropriate signature is known as a keyed-hash message authentication code (HMAC).</span></span> <span data-ttu-id="60fce-132">HMAC różni się od sumy kontrolnej tym, że zajmuje tajny klucz, znany tylko osobie produkującej HMAC i osobie zatwierdzającej go.</span><span class="sxs-lookup"><span data-stu-id="60fce-132">An HMAC differs from a checksum in that it takes a secret key, known only to the person producing the HMAC and to the person validating it.</span></span> <span data-ttu-id="60fce-133">Bez posiadania klucza, nie można produkować poprawne HMAC.</span><span class="sxs-lookup"><span data-stu-id="60fce-133">Without possession of the key, you can't produce a correct HMAC.</span></span> <span data-ttu-id="60fce-134">Po otrzymaniu danych należy wziąć zaszyfrowane dane, niezależnie obliczyć HMAC przy użyciu klucza tajnego, który ty i udział nadawcy, a następnie porównać HMAC, który wysłali z tym, który został obliczony.</span><span class="sxs-lookup"><span data-stu-id="60fce-134">When you receive your data, you'd take the encrypted data, independently compute the HMAC using the secret key you and the sender share, then compare the HMAC they sent against the one you computed.</span></span> <span data-ttu-id="60fce-135">To porównanie musi być stałym czasem, w przeciwnym razie dodano inną wykrywalną wyrocznię, umożliwiając ą inny typ ataku.</span><span class="sxs-lookup"><span data-stu-id="60fce-135">This comparison must be constant time, otherwise you've added another detectable oracle, allowing a different type of attack.</span></span>

<span data-ttu-id="60fce-136">Podsumowując, aby bezpiecznie używać wyściełanych szyfrów bloków CBC, należy połączyć je z hmac (lub innym sprawdzaniem integralności danych), które można sprawdzić przy użyciu stałego porównania czasu przed próbą odszyfrowania danych.</span><span class="sxs-lookup"><span data-stu-id="60fce-136">In summary, to use padded CBC block ciphers safely, you must combine them with an HMAC (or another data integrity check) that you validate using a constant time comparison before trying to decrypt the data.</span></span> <span data-ttu-id="60fce-137">Ponieważ wszystkie zmienione wiadomości zajmują tyle samo czasu, aby wygenerować odpowiedź, atak jest zapobiegany.</span><span class="sxs-lookup"><span data-stu-id="60fce-137">Since all altered messages take the same amount time to produce a response, the attack is prevented.</span></span>

## <a name="who-is-vulnerable"></a><span data-ttu-id="60fce-138">Kto jest podatny na zagrożenia</span><span class="sxs-lookup"><span data-stu-id="60fce-138">Who is vulnerable</span></span>

<span data-ttu-id="60fce-139">Ta luka dotyczy zarówno aplikacji zarządzanych, jak i natywnych, które wykonują własne szyfrowanie i odszyfrowywanie.</span><span class="sxs-lookup"><span data-stu-id="60fce-139">This vulnerability applies to both managed and native applications that are performing their own encryption and decryption.</span></span> <span data-ttu-id="60fce-140">Obejmuje to na przykład:</span><span class="sxs-lookup"><span data-stu-id="60fce-140">This includes, for example:</span></span>

- <span data-ttu-id="60fce-141">Aplikacja, która szyfruje plik cookie do późniejszego odszyfrowywania na serwerze.</span><span class="sxs-lookup"><span data-stu-id="60fce-141">An application that encrypts a cookie for later decryption on the server.</span></span>
- <span data-ttu-id="60fce-142">Aplikacja bazy danych, która zapewnia użytkownikom możliwość wstawiania danych do tabeli, której kolumny są później odszyfrowywane.</span><span class="sxs-lookup"><span data-stu-id="60fce-142">A database application that provides the ability for users to insert data into a table whose columns are later decrypted.</span></span>
- <span data-ttu-id="60fce-143">Aplikacja do przesyłania danych, która opiera się na szyfrowaniu przy użyciu klucza udostępnionego w celu ochrony danych podczas przesyłania.</span><span class="sxs-lookup"><span data-stu-id="60fce-143">A data transfer application that relies on encryption using a shared key to protect the data in transit.</span></span>
- <span data-ttu-id="60fce-144">Aplikacja, która szyfruje i odszyfrowuje wiadomości "wewnątrz" tunelu TLS.</span><span class="sxs-lookup"><span data-stu-id="60fce-144">An application that encrypts and decrypts messages "inside" the TLS tunnel.</span></span>

<span data-ttu-id="60fce-145">Należy pamiętać, że przy użyciu samego protokołu TLS może nie chronić cię w tych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="60fce-145">Note that using TLS alone may not protect you in these scenarios.</span></span>

<span data-ttu-id="60fce-146">Aplikacja podatna na ataki:</span><span class="sxs-lookup"><span data-stu-id="60fce-146">A vulnerable application:</span></span>

- <span data-ttu-id="60fce-147">Odszyfrowuje dane przy użyciu trybu szyfrowania CBC z weryfikowalnym trybem dopełnienia, takim jak PKCS#7 lub ANSI X.923.</span><span class="sxs-lookup"><span data-stu-id="60fce-147">Decrypts data using the CBC cipher mode with a verifiable padding mode, such as PKCS#7 or ANSI X.923.</span></span>
- <span data-ttu-id="60fce-148">Wykonuje odszyfrowywanie bez przeprowadzania sprawdzania integralności danych (za pomocą maca lub asymetrycznego podpisu cyfrowego).</span><span class="sxs-lookup"><span data-stu-id="60fce-148">Performs the decryption without having performed a data integrity check (via a MAC or an asymmetric digital signature).</span></span>

<span data-ttu-id="60fce-149">Dotyczy to również aplikacji zbudowanych na abstrakcjach nad tymi pierwotnymi, takich jak struktura Koperta wiadomości kryptograficznych (PKCS#7/CMS).</span><span class="sxs-lookup"><span data-stu-id="60fce-149">This also applies to applications built on top of abstractions over top of these primitives, such as the Cryptographic Message Syntax (PKCS#7/CMS) EnvelopedData structure.</span></span>

## <a name="related-areas-of-concern"></a><span data-ttu-id="60fce-150">Powiązane obszary budzące obawy</span><span class="sxs-lookup"><span data-stu-id="60fce-150">Related areas of concern</span></span>

<span data-ttu-id="60fce-151">Badania doprowadziły Microsoft być dalej zaniepokojony wiadomości CBC, które są wyściełane iso 10126 równoważne dopełnienia, gdy wiadomość ma dobrze znaną lub przewidywalną strukturę stopki.</span><span class="sxs-lookup"><span data-stu-id="60fce-151">Research has led Microsoft to be further concerned about CBC messages that are padded with ISO 10126-equivalent padding when the message has a well-known or predictable footer structure.</span></span> <span data-ttu-id="60fce-152">Na przykład zawartość przygotowana zgodnie z regułami W3C XML Encryption Syntax and Processing Recommendation (xmlenc, EncryptedXml).</span><span class="sxs-lookup"><span data-stu-id="60fce-152">For example, content prepared under the rules of the W3C XML Encryption Syntax and Processing Recommendation (xmlenc, EncryptedXml).</span></span> <span data-ttu-id="60fce-153">Podczas gdy wskazówki W3C do podpisania wiadomości następnie szyfrowania uznano za odpowiednie w tym czasie, Microsoft zaleca teraz zawsze robi szyfrowania, a następnie znak.</span><span class="sxs-lookup"><span data-stu-id="60fce-153">While the W3C guidance to sign the message then encrypt was considered appropriate at the time, Microsoft now recommends always doing encrypt-then-sign.</span></span>

<span data-ttu-id="60fce-154">Deweloperzy aplikacji zawsze powinni mieć na uwadze sprawdzanie możliwości zastosowania asymetrycznego klucza podpisu, ponieważ nie ma nieodłącznej relacji zaufania między kluczem asymetrycznym a dowolną wiadomością.</span><span class="sxs-lookup"><span data-stu-id="60fce-154">Application developers should always be mindful of verifying the applicability of an asymmetric signature key, as there's no inherent trust relationship between an asymmetric key and an arbitrary message.</span></span>

## <a name="details"></a><span data-ttu-id="60fce-155">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="60fce-155">Details</span></span>

<span data-ttu-id="60fce-156">Historycznie istniała zgoda co do tego, że ważne jest, aby zarówno szyfrować, jak i uwierzytelniać ważne dane przy użyciu środków, takich jak podpisy HMAC lub RSA.</span><span class="sxs-lookup"><span data-stu-id="60fce-156">Historically, there has been consensus that it's important to both encrypt and authenticate important data, using means such as HMAC or RSA signatures.</span></span> <span data-ttu-id="60fce-157">Jednak było mniej jasne wskazówki dotyczące sposobu sekwencjonowania operacji szyfrowania i uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="60fce-157">However, there has been less clear guidance as to how to sequence the encryption and authentication operations.</span></span> <span data-ttu-id="60fce-158">Ze względu na lukę w zabezpieczeniach wyszczególnioną w tym artykule wskazówki firmy Microsoft są teraz zawsze używane do paradygmatu "szyfrowanie, a następnie znak".</span><span class="sxs-lookup"><span data-stu-id="60fce-158">Due to the vulnerability detailed in this article, Microsoft's guidance is now to always use the "encrypt-then-sign" paradigm.</span></span> <span data-ttu-id="60fce-159">Oznacza to, że najpierw zaszyfruj dane przy użyciu klucza symetrycznego, a następnie obłamuje podpis MAC lub asymetryczny za pomocą szyfru (zaszyfrowanych danych).</span><span class="sxs-lookup"><span data-stu-id="60fce-159">That is, first encrypt data using a symmetric key, then compute a MAC or asymmetric signature over the ciphertext (encrypted data).</span></span> <span data-ttu-id="60fce-160">Podczas odszyfrowywania danych wykonaj odwrotnie.</span><span class="sxs-lookup"><span data-stu-id="60fce-160">When decrypting data, perform the reverse.</span></span> <span data-ttu-id="60fce-161">Najpierw potwierdź MAC lub podpis szyfru, a następnie odszyfruj go.</span><span class="sxs-lookup"><span data-stu-id="60fce-161">First, confirm the MAC or signature of the ciphertext, then decrypt it.</span></span>

<span data-ttu-id="60fce-162">Wiadomo, że od ponad 10 lat istnieje klasa luk w zabezpieczeniach znana jako "ataki wyroczni" dopełnianie.</span><span class="sxs-lookup"><span data-stu-id="60fce-162">A class of vulnerabilities known as "padding oracle attacks" have been known to exist for over 10 years.</span></span> <span data-ttu-id="60fce-163">Luki te umożliwiają osobie atakującej odszyfrowanie danych zaszyfrowanych za pomocą symetrycznych algorytmów blokowych, takich jak AES i 3DES, przy użyciu nie więcej niż 4096 prób na blok danych.</span><span class="sxs-lookup"><span data-stu-id="60fce-163">These vulnerabilities allow an attacker to decrypt data encrypted by symmetric block algorithms, such as AES and 3DES, using no more than 4096 attempts per block of data.</span></span> <span data-ttu-id="60fce-164">Luki te wykorzystują fakt, że szyfry blokowe są najczęściej używane z weryfikowalnymi danymi dopełnienia na końcu.</span><span class="sxs-lookup"><span data-stu-id="60fce-164">These vulnerabilities make use of the fact that block ciphers are most frequently used with verifiable padding data at the end.</span></span> <span data-ttu-id="60fce-165">Stwierdzono, że jeśli osoba atakująca może manipulować szyfrem i dowiedzieć się, czy naruszenie spowodowało błąd w formacie dopełnienia na końcu, osoba atakująca może odszyfrować dane.</span><span class="sxs-lookup"><span data-stu-id="60fce-165">It was found that if an attacker can tamper with ciphertext and find out whether the tampering caused an error in the format of the padding at the end, the attacker can decrypt the data.</span></span>

<span data-ttu-id="60fce-166">Początkowo praktyczne ataki były oparte na usługach, które zwracałyby różne kody błędów w zależności od tego, czy dopełnienie było prawidłowe, takie jak ASP.NET luka [MS10-070](/security-updates/SecurityBulletins/2010/ms10-070).</span><span class="sxs-lookup"><span data-stu-id="60fce-166">Initially, practical attacks were based on services that would return different error codes based on whether padding was valid, such as the ASP.NET vulnerability [MS10-070](/security-updates/SecurityBulletins/2010/ms10-070).</span></span> <span data-ttu-id="60fce-167">Jednak Microsoft uważa teraz, że jest to praktyczne do przeprowadzenia podobnych ataków przy użyciu tylko różnice w czasie między przetwarzania prawidłowe i nieprawidłowe dopełnienia.</span><span class="sxs-lookup"><span data-stu-id="60fce-167">However, Microsoft now believes that it's practical to conduct similar attacks using only the differences in timing between processing valid and invalid padding.</span></span>

<span data-ttu-id="60fce-168">Pod warunkiem, że schemat szyfrowania wykorzystuje podpis i że weryfikacja podpisu jest wykonywana ze stałym czasem wykonywania dla danej długości danych (niezależnie od zawartości), integralność danych może być zweryfikowana bez emitowania jakichkolwiek informacji osobie atakującej za pośrednictwem [kanału bocznego](https://en.wikipedia.org/wiki/Side-channel_attack).</span><span class="sxs-lookup"><span data-stu-id="60fce-168">Provided that the encryption scheme employs a signature and that the signature verification is performed with a fixed runtime for a given length of data (irrespective of the contents), the data integrity can be verified without emitting any information to an attacker via a [side channel](https://en.wikipedia.org/wiki/Side-channel_attack).</span></span> <span data-ttu-id="60fce-169">Ponieważ sprawdzanie integralności odrzuca wszelkie zmodyfikowane wiadomości, zagrożenie oracle dopełnianie jest złagodzone.</span><span class="sxs-lookup"><span data-stu-id="60fce-169">Since the integrity check rejects any tampered messages, the padding oracle threat is mitigated.</span></span>

## <a name="guidance"></a><span data-ttu-id="60fce-170">Wskazówki</span><span class="sxs-lookup"><span data-stu-id="60fce-170">Guidance</span></span>

<span data-ttu-id="60fce-171">Przede wszystkim firma Microsoft zaleca, aby wszelkie dane, które mają poufność, były przesyłane za pośrednictwem protokołu TLS (Transport Layer Security), następcy aplikacji Secure Sockets Layer (SSL).</span><span class="sxs-lookup"><span data-stu-id="60fce-171">First and foremost, Microsoft recommends that any data that has confidentiality needs be transmitted over Transport Layer Security (TLS), the successor to Secure Sockets Layer (SSL).</span></span>

<span data-ttu-id="60fce-172">Następnie przeanalizuj aplikację, aby:</span><span class="sxs-lookup"><span data-stu-id="60fce-172">Next, analyze your application to:</span></span>

- <span data-ttu-id="60fce-173">Dokładnie dowiedz się, jakie szyfrowanie wykonujesz i jakie szyfrowanie jest dostarczane przez platformy i interfejsy API, których używasz.</span><span class="sxs-lookup"><span data-stu-id="60fce-173">Understand precisely what encryption you're performing and what encryption is being provided by the platforms and APIs you're using.</span></span>
- <span data-ttu-id="60fce-174">Upewnij się, że każde użycie w każdej warstwie [algorytmu szyfrowania bloku](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers)symetrycznego , takiego jak AES i 3DES, w trybie CBC obejmuje użycie sprawdzania integralności danych z kluczem tajnym (podpis asymetryczny, HMAC lub w celu zmiany trybu szyfrowania na tryb [uwierzytelniania szyfrowania](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE), takiego jak GCM lub CCM).</span><span class="sxs-lookup"><span data-stu-id="60fce-174">Be certain that each usage at each layer of a symmetric [block cipher algorithm](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), such as AES and 3DES, in CBC mode incorporate the use of a secret-keyed data integrity check (an asymmetric signature, an HMAC, or to change the cipher mode to an [authenticated encryption](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE) mode such as GCM or CCM).</span></span>

<span data-ttu-id="60fce-175">Na podstawie bieżących badań, ogólnie uważa się, że gdy kroki uwierzytelniania i szyfrowania są wykonywane niezależnie dla trybów szyfrowania innych niż AE, uwierzytelnianie szyfrowania (szyfrowanie,a następnie znak) jest najlepszym rozwiązaniem ogólnym.</span><span class="sxs-lookup"><span data-stu-id="60fce-175">Based on the current research, it's generally believed that when the authentication and encryption steps are performed independently for non-AE modes of encryption, authenticating the ciphertext (encrypt-then-sign) is the best general option.</span></span> <span data-ttu-id="60fce-176">Jednak nie ma jednej uniwersalnej poprawnej odpowiedzi na kryptografię, a to uogólnienie nie jest tak dobre, jak skierowane porady profesjonalnego kryptografa.</span><span class="sxs-lookup"><span data-stu-id="60fce-176">However, there's no one-size-fits-all correct answer to cryptography and this generalization isn't as good as directed advice from a professional cryptographer.</span></span>

<span data-ttu-id="60fce-177">Aplikacje, które nie mogą zmienić formatu obsługi wiadomości, ale wykonują nieuwierzytelnione odszyfrowywanie CBC, są zachęcane do próby włączenia czynników ograniczających zagrożenie, takich jak:</span><span class="sxs-lookup"><span data-stu-id="60fce-177">Applications that are unable to change their messaging format but perform unauthenticated CBC decryption are encouraged to try to incorporate mitigations such as:</span></span>

- <span data-ttu-id="60fce-178">Odszyfruj bez zezwolenia deszyfratorowi na weryfikację lub usunięcie dopełnienia:</span><span class="sxs-lookup"><span data-stu-id="60fce-178">Decrypt without allowing the decryptor to verify or remove padding:</span></span>
  - <span data-ttu-id="60fce-179">Wszelkie dopełnienie, które zostały zastosowane nadal musi zostać usunięty lub zignorowany, przenosisz obciążenie do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="60fce-179">Any padding that was applied still needs to be removed or ignored, you're moving the burden into your application.</span></span>
  - <span data-ttu-id="60fce-180">Zaletą jest to, że weryfikacja i usuwanie dopełnienia mogą być włączone do innej logiki weryfikacji danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="60fce-180">The benefit is that the padding verification and removal can be incorporated into other application data verification logic.</span></span> <span data-ttu-id="60fce-181">Jeśli weryfikacja dopełnienia i weryfikacja danych mogą być wykonywane w stałym czasie, zagrożenie jest zmniejszone.</span><span class="sxs-lookup"><span data-stu-id="60fce-181">If the padding verification and data verification can be done in constant time, the threat is reduced.</span></span>
  - <span data-ttu-id="60fce-182">Ponieważ interpretacja dopełnienie zmienia długość wiadomości postrzegane, nadal mogą istnieć informacje o czasie emitowane z tego podejścia.</span><span class="sxs-lookup"><span data-stu-id="60fce-182">Since the interpretation of the padding changes the perceived message length, there may still be timing information emitted from this approach.</span></span>
- <span data-ttu-id="60fce-183">Zmień tryb dopełnienia odszyfrowywania na ISO10126:</span><span class="sxs-lookup"><span data-stu-id="60fce-183">Change the decryption padding mode to ISO10126:</span></span>
  - <span data-ttu-id="60fce-184">Dopełnienie deszyfrujące ISO10126 jest zgodne zarówno z dopełnieniem szyfrowania PKCS7, jak i dopełnieniem szyfrowania ANSIX923.</span><span class="sxs-lookup"><span data-stu-id="60fce-184">ISO10126 decryption padding is compatible with both PKCS7 encryption padding and ANSIX923 encryption padding.</span></span>
  - <span data-ttu-id="60fce-185">Zmiana trybu zmniejsza dopełnienie oracle wiedzy do 1 bajt zamiast całego bloku.</span><span class="sxs-lookup"><span data-stu-id="60fce-185">Changing the mode reduces the padding oracle knowledge to 1 byte instead of the entire block.</span></span> <span data-ttu-id="60fce-186">Jeśli jednak zawartość ma dobrze znaną stopkę, taką jak zamykający element XML, powiązane ataki mogą nadal atakować pozostałą część wiadomości.</span><span class="sxs-lookup"><span data-stu-id="60fce-186">However, if the content has a well-known footer, such as a closing XML element, related attacks can continue to attack the rest of the message.</span></span>
  - <span data-ttu-id="60fce-187">Nie uniemożliwia to również odzyskiwania zwykłego tekstu w sytuacjach, gdy osoba atakująca może zmuszać ten sam zwykły tekst do wielokrotnego szyfrowania za pomocą innego przesunięcia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="60fce-187">This also doesn't prevent plaintext recovery in situations where the attacker can coerce the same plaintext to be encrypted multiple times with a different message offset.</span></span>
- <span data-ttu-id="60fce-188">Gate oceny wywołania odszyfrowywania, aby tłumić sygnał rozrządu:</span><span class="sxs-lookup"><span data-stu-id="60fce-188">Gate the evaluation of a decryption call to dampen the timing signal:</span></span>
  - <span data-ttu-id="60fce-189">Obliczenia czasu wstrzymania musi mieć minimum powyżej maksymalnej ilości czasu operacji odszyfrowywania zajmie dla dowolnego segmentu danych, który zawiera dopełnienie.</span><span class="sxs-lookup"><span data-stu-id="60fce-189">The computation of hold time must have a minimum in excess of the maximum amount of time the decryption operation would take for any data segment that contains padding.</span></span>
  - <span data-ttu-id="60fce-190">Obliczenia czasu powinny być wykonywane zgodnie ze wskazówkami w [Uzyskiwanie sygnatury czasowe o wysokiej rozdzielczości,](/windows/desktop/sysinfo/acquiring-high-resolution-time-stamps)a nie za pomocą <xref:System.Environment.TickCount?displayProperty=nameWithType> (z zastrzeżeniem roll-over/overflow) lub odejmowanie dwóch sygnatury czasowe systemu (z zastrzeżeniem błędów regulacji NTP).</span><span class="sxs-lookup"><span data-stu-id="60fce-190">Time computations should be done according to the guidance in [Acquiring high-resolution time stamps](/windows/desktop/sysinfo/acquiring-high-resolution-time-stamps), not by using <xref:System.Environment.TickCount?displayProperty=nameWithType> (subject to roll-over/overflow) or subtracting two system timestamps (subject to NTP adjustment errors).</span></span>
  - <span data-ttu-id="60fce-191">Obliczenia czasu musi zawierać operacji odszyfrowywania, w tym wszystkie potencjalne wyjątki w zarządzanych lub aplikacji C++, a nie tylko wyściełane na końcu.</span><span class="sxs-lookup"><span data-stu-id="60fce-191">Time computations must be inclusive of the decryption operation including all potential exceptions in managed or C++ applications, not just padded onto the end.</span></span>
  - <span data-ttu-id="60fce-192">Jeśli sukces lub niepowodzenie zostało jeszcze ustalone, brama chronometrażu musi zwrócić błąd po wygaśnięciu.</span><span class="sxs-lookup"><span data-stu-id="60fce-192">If success or failure has been determined yet, the timing gate needs to return failure when it expires.</span></span>
- <span data-ttu-id="60fce-193">Usługi, które wykonują nieuwierzytelnione odszyfrowywanie powinny mieć monitorowanie w celu wykrycia, że zalew "nieprawidłowych" komunikatów przeszła.</span><span class="sxs-lookup"><span data-stu-id="60fce-193">Services that are performing unauthenticated decryption should have monitoring in place to detect that a flood of "invalid" messages has come through.</span></span>
  - <span data-ttu-id="60fce-194">Należy pamiętać, że sygnał ten niesie zarówno fałszywe alarmy (legalnie uszkodzone dane), jak i fałszywe negatywy (rozprzestrzenianie ataku na wystarczająco długi czas, aby uniknąć wykrycia).</span><span class="sxs-lookup"><span data-stu-id="60fce-194">Bear in mind that this signal carries both false positives (legitimately corrupted data) and false negatives (spreading out the attack over a sufficiently long time to evade detection).</span></span>

## <a name="finding-vulnerable-code---native-applications"></a><span data-ttu-id="60fce-195">Znajdowanie kodu podlegania usterce — aplikacje natywne</span><span class="sxs-lookup"><span data-stu-id="60fce-195">Finding vulnerable code - native applications</span></span>

<span data-ttu-id="60fce-196">Dla programów zbudowanych na przeciwko windows kryptografii: Nowej Generacji (CNG) biblioteki:</span><span class="sxs-lookup"><span data-stu-id="60fce-196">For programs built against the Windows Cryptography: Next Generation (CNG) library:</span></span>

- <span data-ttu-id="60fce-197">Wywołanie odszyfrowywania jest [BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt), `BCRYPT_BLOCK_PADDING` określając flagę.</span><span class="sxs-lookup"><span data-stu-id="60fce-197">The decryption call is to [BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt), specifying the `BCRYPT_BLOCK_PADDING` flag.</span></span>
- <span data-ttu-id="60fce-198">Dojście klucza zostało zainicjowane przez [BCRYPT_CHAINING_MODE](/windows/desktop/SecCNG/cng-property-identifiers#BCRYPT_CHAINING_MODE) wywołanie `BCRYPT_CHAIN_MODE_CBC` [BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty) z BCRYPT_CHAINING_MODE ustawionym na .</span><span class="sxs-lookup"><span data-stu-id="60fce-198">The key handle has been initialized by calling [BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty) with [BCRYPT_CHAINING_MODE](/windows/desktop/SecCNG/cng-property-identifiers#BCRYPT_CHAINING_MODE) set to `BCRYPT_CHAIN_MODE_CBC`.</span></span>
  - <span data-ttu-id="60fce-199">Ponieważ `BCRYPT_CHAIN_MODE_CBC` jest to wartość domyślna, kod, `BCRYPT_CHAINING_MODE`którego dotyczy problem, może nie przypisać żadnej wartości dla .</span><span class="sxs-lookup"><span data-stu-id="60fce-199">Since `BCRYPT_CHAIN_MODE_CBC` is the default, affected code may not have assigned any value for `BCRYPT_CHAINING_MODE`.</span></span>

<span data-ttu-id="60fce-200">W przypadku programów utworzonych w ramach starszego kryptograficznego interfejsu API systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="60fce-200">For programs built against the older Windows Cryptographic API:</span></span>

- <span data-ttu-id="60fce-201">Wywołanie odszyfrowywania jest [CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) z `Final=TRUE`.</span><span class="sxs-lookup"><span data-stu-id="60fce-201">The decryption call is to [CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) with `Final=TRUE`.</span></span>
- <span data-ttu-id="60fce-202">Dojście klucza zostało zainicjowane przez wywołanie [CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam) z [KP_MODE](/windows/desktop/api/wincrypt/nf-wincrypt-cryptgetkeyparam) ustawionym na `CRYPT_MODE_CBC`.</span><span class="sxs-lookup"><span data-stu-id="60fce-202">The key handle has been initialized by calling [CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam) with [KP_MODE](/windows/desktop/api/wincrypt/nf-wincrypt-cryptgetkeyparam) set to `CRYPT_MODE_CBC`.</span></span>
  - <span data-ttu-id="60fce-203">Ponieważ `CRYPT_MODE_CBC` jest to wartość domyślna, kod, `KP_MODE`którego dotyczy problem, może nie przypisać żadnej wartości dla .</span><span class="sxs-lookup"><span data-stu-id="60fce-203">Since `CRYPT_MODE_CBC` is the default, affected code may not have assigned any value for `KP_MODE`.</span></span>

## <a name="finding-vulnerable-code---managed-applications"></a><span data-ttu-id="60fce-204">Znajdowanie kodu podlegania usterce — aplikacje zarządzane</span><span class="sxs-lookup"><span data-stu-id="60fce-204">Finding vulnerable code - managed applications</span></span>

- <span data-ttu-id="60fce-205">Wywołanie odszyfrowywania jest <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> do lub <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>metody na .</span><span class="sxs-lookup"><span data-stu-id="60fce-205">The decryption call is to the <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> or <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> methods on <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="60fce-206">Obejmuje to następujące typy pochodne w ramach .NET, ale może również obejmować typy innych firm:</span><span class="sxs-lookup"><span data-stu-id="60fce-206">This includes the following derived types within the .NET, but may also include third-party types:</span></span>
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
- <span data-ttu-id="60fce-207">Właściwość <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> została ustawiona <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>na <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>, lub .</span><span class="sxs-lookup"><span data-stu-id="60fce-207">The <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> property was set to <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>, or <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="60fce-208">Ponieważ <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> jest to wartość domyślna, kod, którego dotyczy problem, może nigdy nie przypisał <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="60fce-208">Since <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> is the default, affected code may never have assigned the <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> property.</span></span>
- <span data-ttu-id="60fce-209">Obiekt <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> został ustawiony na<xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="60fce-209">The <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> property was set to <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType></span></span>
  - <span data-ttu-id="60fce-210">Ponieważ <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> jest to wartość domyślna, kod, którego dotyczy problem, może nigdy nie przypisał <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="60fce-210">Since <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> is the default, affected code may never have assigned the <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> property.</span></span>

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a><span data-ttu-id="60fce-211">Znajdowanie zagrożonego kodu — składnia wiadomości kryptograficznych</span><span class="sxs-lookup"><span data-stu-id="60fce-211">Finding vulnerable code - cryptographic message syntax</span></span>

<span data-ttu-id="60fce-212">Nieuwierzytelniony komunikat CMS EnvelopedData, którego zaszyfrowana zawartość korzysta z trybu CBC AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) lub RC2 (1.2.840.113549.3.2) jest wrażliwych, a także wiadomości przy użyciu innych algorytmów szyfrowania blokowego w trybie CBC.</span><span class="sxs-lookup"><span data-stu-id="60fce-212">An unauthenticated CMS EnvelopedData message whose encrypted content uses the CBC mode of AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) or RC2 (1.2.840.113549.3.2) is vulnerable, as well as messages using any other block cipher algorithms in CBC mode.</span></span>

<span data-ttu-id="60fce-213">Szyfry strumienia nie są podatne na tę szczególną lukę w zabezpieczeniach, firma Microsoft zaleca zawsze uwierzytelnianie danych za pomocą sprawdzania wartości ContentEncryptionAlgorithm.</span><span class="sxs-lookup"><span data-stu-id="60fce-213">While stream ciphers aren't susceptible to this particular vulnerability, Microsoft recommends always authenticating the data over inspecting the ContentEncryptionAlgorithm value.</span></span>

<span data-ttu-id="60fce-214">W przypadku aplikacji zarządzanych obiekt blob CMS EnvelopedData można <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>wykryć jako dowolną wartość, która jest przekazywana do .</span><span class="sxs-lookup"><span data-stu-id="60fce-214">For managed applications, a CMS EnvelopedData blob can be detected as any value that is passed to <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.</span></span>

<span data-ttu-id="60fce-215">W przypadku aplikacji natywnych obiekt blob CMS EnvelopedData można wykryć jako dowolną [CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam) wartość `CMSG_ENVELOPED` dostarczoną do dojścia CMS za pośrednictwem [CryptMsgUpdate,](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) którego wynikowy CMSG_TYPE_PARAM jest i/lub dojście CMS jest później wysyłane instrukcję `CMSG_CTRL_DECRYPT` za pośrednictwem [CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol).</span><span class="sxs-lookup"><span data-stu-id="60fce-215">For native applications, a CMS EnvelopedData blob can be detected as any value provided to a CMS handle via [CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) whose resulting [CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam) is `CMSG_ENVELOPED` and/or the CMS handle is later sent a `CMSG_CTRL_DECRYPT` instruction via [CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol).</span></span>

## <a name="vulnerable-code-example---managed"></a><span data-ttu-id="60fce-216">Przykład kodu podatny na zagrożenia — zarządzany</span><span class="sxs-lookup"><span data-stu-id="60fce-216">Vulnerable code example - managed</span></span>

<span data-ttu-id="60fce-217">Ta metoda odczytuje plik cookie i odszyfrowuje go, a kontrola integralności danych nie jest widoczna.</span><span class="sxs-lookup"><span data-stu-id="60fce-217">This method reads a cookie and decrypts it and no data integrity check is visible.</span></span> <span data-ttu-id="60fce-218">W związku z tym zawartość pliku cookie odczytywanego przez tę metodę może zostać zaatakowana przez użytkownika, który go otrzymał, lub przez osobę atakującą, która uzyskała zaszyfrowaną wartość pliku cookie.</span><span class="sxs-lookup"><span data-stu-id="60fce-218">Therefore, the contents of a cookie that is read by this method can be attacked by the user who received it, or by any attacker who has obtained the encrypted cookie value.</span></span>

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

## <a name="example-code-following-recommended-practices---managed"></a><span data-ttu-id="60fce-219">Przykładowy kod po zalecanych praktykach — zarządzany</span><span class="sxs-lookup"><span data-stu-id="60fce-219">Example code following recommended practices - managed</span></span>

<span data-ttu-id="60fce-220">Poniższy przykładowy kod używa niestandardowego formatu wiadomości</span><span class="sxs-lookup"><span data-stu-id="60fce-220">The following sample code uses a non-standard message format of</span></span>

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

<span data-ttu-id="60fce-221">gdzie `cipher_algorithm_id` identyfikatory i `hmac_algorithm_id` algorytmsą lokalnymi (niestandardowymi) reprezentacjami tych algorytmów.</span><span class="sxs-lookup"><span data-stu-id="60fce-221">where the `cipher_algorithm_id` and `hmac_algorithm_id` algorithm identifiers are application-local (non-standard) representations of those algorithms.</span></span> <span data-ttu-id="60fce-222">Identyfikatory te mogą mieć sens w innych częściach istniejącego protokołu obsługi wiadomości, a nie jako gołe połączony bytestream.</span><span class="sxs-lookup"><span data-stu-id="60fce-222">These identifiers may make sense in other parts of your existing messaging protocol instead of as a bare concatenated bytestream.</span></span>

<span data-ttu-id="60fce-223">W tym przykładzie użyto również pojedynczego klucza głównego do uzyskania zarówno klucza szyfrowania, jak i klucza HMAC.</span><span class="sxs-lookup"><span data-stu-id="60fce-223">This example also uses a single master key to derive both an encryption key and an HMAC key.</span></span> <span data-ttu-id="60fce-224">Jest to zarówno jako wygoda dla przełączania aplikacji z singly-keyed do aplikacji z dwoma kluczami, jak i zachęcanie do zachowania dwóch kluczy jako różnych wartości.</span><span class="sxs-lookup"><span data-stu-id="60fce-224">This is provided both as a convenience for turning a singly-keyed application into a dual-keyed application, and to encourage keeping the two keys as different values.</span></span> <span data-ttu-id="60fce-225">Ponadto gwarantuje, że klucz HMAC i klucz szyfrowania nie mogą wydostać się z synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="60fce-225">It further guarantees that the HMAC key and encryption key can't get out of synchronization.</span></span>

<span data-ttu-id="60fce-226">W tym przykładzie nie <xref:System.IO.Stream> akceptuje szyfrowania lub odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="60fce-226">This sample doesn't accept a <xref:System.IO.Stream> for either encryption or decryption.</span></span> <span data-ttu-id="60fce-227">Bieżący format danych utrudnia szyfrowanie jednoprzebiegowe, `hmac_tag` ponieważ wartość poprzedza szyfrtekst.</span><span class="sxs-lookup"><span data-stu-id="60fce-227">The current data format makes one-pass encrypt difficult because the `hmac_tag` value precedes the ciphertext.</span></span> <span data-ttu-id="60fce-228">Jednak ten format został wybrany, ponieważ zachowuje wszystkie elementy o stałym rozmiarze na początku, aby uprościć analizator.</span><span class="sxs-lookup"><span data-stu-id="60fce-228">However, this format was chosen because it keeps all of the fixed-size elements at the beginning to keep the parser simpler.</span></span> <span data-ttu-id="60fce-229">W tym formacie danych, one-pass odszyfrowywania jest możliwe, choć realizator jest ostrzegany, aby wywołać GetHashAndReset i sprawdzić wynik przed wywołaniem TransformFinalBlock.</span><span class="sxs-lookup"><span data-stu-id="60fce-229">With this data format, one-pass decrypt is possible, though an implementer is cautioned to call GetHashAndReset and verify the result before calling TransformFinalBlock.</span></span> <span data-ttu-id="60fce-230">Jeśli szyfrowanie przesyłania strumieniowego jest ważne, może być wymagany inny tryb AE.</span><span class="sxs-lookup"><span data-stu-id="60fce-230">If streaming encryption is important, then a different AE mode may be required.</span></span>

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
