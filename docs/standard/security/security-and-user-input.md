---
title: Zabezpieczenia i dane użytkownika
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
ms.openlocfilehash: 0d34b06b44241feb7d6e3c8f76447b861563cfdc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705863"
---
# <a name="security-and-user-input"></a><span data-ttu-id="15aee-102">Zabezpieczenia i dane użytkownika</span><span class="sxs-lookup"><span data-stu-id="15aee-102">Security and User Input</span></span>

<span data-ttu-id="15aee-103">Dane użytkownika, czyli dowolny rodzaj danych wejściowych (dane z żądania sieci Web lub adresu URL, dane wejściowe do kontrolek aplikacji Microsoft Windows Forms itd.), mogą mieć negatywny wpływ na kod, ponieważ często dane są używane bezpośrednio jako parametry wywołania innego kodu.</span><span class="sxs-lookup"><span data-stu-id="15aee-103">User data, which is any kind of input (data from a Web request or URL, input to controls of a Microsoft Windows Forms application, and so on), can adversely influence code because often that data is used directly as parameters to call other code.</span></span> <span data-ttu-id="15aee-104">Ta sytuacja jest analogiczna do złośliwego kodu wywołującego kod przy użyciu dziwnych parametrów i należy podjąć te same środki ostrożności.</span><span class="sxs-lookup"><span data-stu-id="15aee-104">This situation is analogous to malicious code calling your code with strange parameters, and the same precautions should be taken.</span></span> <span data-ttu-id="15aee-105">Dane wejściowe użytkownika są naprawdę trudniejsze do zagwarantowania, ponieważ nie ma ramki stosu do śledzenia obecności potencjalnie niezaufanych danych.</span><span class="sxs-lookup"><span data-stu-id="15aee-105">User input is actually harder to make safe because there is no stack frame to trace the presence of the potentially untrusted data.</span></span>

<span data-ttu-id="15aee-106">Znajdują się one wśród delikatnych i najtrudniejszych usterek związanych z bezpieczeństwem, które mogą znajdować się w kodzie, który wydaje się niezwiązany z zabezpieczeniami, są bramą do przekazywania nieprawidłowych danych do innego kodu.</span><span class="sxs-lookup"><span data-stu-id="15aee-106">These are among the subtlest and hardest security bugs to find because, although they can exist in code that is seemingly unrelated to security, they are a gateway to pass bad data through to other code.</span></span> <span data-ttu-id="15aee-107">Aby wyszukać te błędy, postępuj zgodnie z dowolnym rodzajem danych wejściowych, Wyobraź sobie, jakie może być zakres możliwych wartości, i rozważ, czy kod, który widzi te dane, może obsłużyć wszystkie te przypadki.</span><span class="sxs-lookup"><span data-stu-id="15aee-107">To look for these bugs, follow any kind of input data, imagine what the range of possible values might be, and consider whether the code seeing this data can handle all those cases.</span></span> <span data-ttu-id="15aee-108">Można naprawić te usterki poprzez sprawdzenie zakresu i odrzucenie wszelkich danych wejściowych, których kod nie może obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="15aee-108">You can fix these bugs through range checking and rejecting any input the code cannot handle.</span></span>

<span data-ttu-id="15aee-109">Poniżej wymieniono istotne zagadnienia dotyczące danych użytkownika:</span><span class="sxs-lookup"><span data-stu-id="15aee-109">Some important considerations involving user data include the following:</span></span>

- <span data-ttu-id="15aee-110">Wszystkie dane użytkownika w odpowiedzi serwera są uruchamiane w kontekście lokacji serwera na kliencie programu.</span><span class="sxs-lookup"><span data-stu-id="15aee-110">Any user data in a server response runs in the context of the server's site on the client.</span></span> <span data-ttu-id="15aee-111">Jeśli serwer sieci Web pobiera dane użytkownika i wstawia je do zwróconej strony sieci Web, może na przykład uwzględnić tag **\<skryptu >** i uruchomić go z serwera.</span><span class="sxs-lookup"><span data-stu-id="15aee-111">If your Web server takes user data and inserts it into the returned Web page, it might, for example, include a **\<script>** tag and run as if from the server.</span></span>

- <span data-ttu-id="15aee-112">Należy pamiętać, że klient może zażądać dowolnego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="15aee-112">Remember that the client can request any URL.</span></span>

- <span data-ttu-id="15aee-113">Weź pod uwagę lewę lub nieprawidłowe ścieżki:</span><span class="sxs-lookup"><span data-stu-id="15aee-113">Consider tricky or invalid paths:</span></span>

  - <span data-ttu-id="15aee-114">.. \, bardzo długie ścieżki.</span><span class="sxs-lookup"><span data-stu-id="15aee-114">..\ , extremely long paths.</span></span>

  - <span data-ttu-id="15aee-115">Użycie znaków wieloznacznych (\*).</span><span class="sxs-lookup"><span data-stu-id="15aee-115">Use of wild card characters (\*).</span></span>

  - <span data-ttu-id="15aee-116">Rozszerzenie tokenu (% token%).</span><span class="sxs-lookup"><span data-stu-id="15aee-116">Token expansion (%token%).</span></span>

  - <span data-ttu-id="15aee-117">Nietypowe formy ścieżek o specjalnym znaczeniu.</span><span class="sxs-lookup"><span data-stu-id="15aee-117">Strange forms of paths with special meaning.</span></span>

  - <span data-ttu-id="15aee-118">Alternatywne nazwy strumieni systemu plików, takie jak `filename::$DATA`.</span><span class="sxs-lookup"><span data-stu-id="15aee-118">Alternate file system stream names such as `filename::$DATA`.</span></span>

  - <span data-ttu-id="15aee-119">Krótkie wersje plików, takie jak `longfi~1` `longfilename`.</span><span class="sxs-lookup"><span data-stu-id="15aee-119">Short versions of file names such as `longfi~1` for `longfilename`.</span></span>

- <span data-ttu-id="15aee-120">Pamiętaj, że w ramach oceny (UserData) można wykonać dowolną czynność.</span><span class="sxs-lookup"><span data-stu-id="15aee-120">Remember that Eval(userdata) can do anything.</span></span>

- <span data-ttu-id="15aee-121">Uważaj na późne wiązanie do nazwy zawierającej pewne dane użytkownika.</span><span class="sxs-lookup"><span data-stu-id="15aee-121">Be wary of late binding to a name that includes some user data.</span></span>

- <span data-ttu-id="15aee-122">W przypadku pracy z danymi w sieci Web należy wziąć pod uwagę różne formy ucieczki, takie jak:</span><span class="sxs-lookup"><span data-stu-id="15aee-122">If you are dealing with Web data, consider the various forms of escapes that are permissible, including:</span></span>

  - <span data-ttu-id="15aee-123">Szesnastkowe znaki ucieczki (% nn).</span><span class="sxs-lookup"><span data-stu-id="15aee-123">Hexadecimal escapes (%nn).</span></span>

  - <span data-ttu-id="15aee-124">Ucieczki Unicode (% NNN).</span><span class="sxs-lookup"><span data-stu-id="15aee-124">Unicode escapes (%nnn).</span></span>

  - <span data-ttu-id="15aee-125">Nadlongowe sekwencje UTF-8 (% nn% nn).</span><span class="sxs-lookup"><span data-stu-id="15aee-125">Overlong UTF-8 escapes (%nn%nn).</span></span>

  - <span data-ttu-id="15aee-126">Podwójne ucieczki (% nn staną się% mmnn, gdzie% mm jest ucieczką dla "%").</span><span class="sxs-lookup"><span data-stu-id="15aee-126">Double escapes (%nn becomes %mmnn, where %mm is the escape for '%').</span></span>

- <span data-ttu-id="15aee-127">Należy ostrożnie wymusić nazwy użytkowników, które mogą mieć więcej niż jeden format kanoniczny.</span><span class="sxs-lookup"><span data-stu-id="15aee-127">Be wary of user names that might have more than one canonical format.</span></span> <span data-ttu-id="15aee-128">Można na przykład użyć formularza\\*nazwy użytkownika* lub *nazwy użytkownika*@mydomain.example.com.</span><span class="sxs-lookup"><span data-stu-id="15aee-128">For example, you can often use either the MYDOMAIN\\*username* form or the *username*@mydomain.example.com form.</span></span>

## <a name="see-also"></a><span data-ttu-id="15aee-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15aee-129">See also</span></span>

- [<span data-ttu-id="15aee-130">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="15aee-130">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
