---
title: Zabezpieczenia i dane użytkownika
description: Kod może przekazać dane wprowadzone przez użytkownika jako parametry do innego kodu, co może mieć wpływ na zabezpieczenia. Sprawdzanie zakresu pozwala odrzucać problematyczne dane wejściowe.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
ms.openlocfilehash: 995af30385790a88718193e7abad1db7bc4b56c3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84275948"
---
# <a name="security-and-user-input"></a><span data-ttu-id="7fd3c-104">Zabezpieczenia i dane użytkownika</span><span class="sxs-lookup"><span data-stu-id="7fd3c-104">Security and User Input</span></span>

<span data-ttu-id="7fd3c-105">Dane użytkownika, czyli dowolny rodzaj danych wejściowych (dane z żądania sieci Web lub adresu URL, dane wejściowe do kontrolek aplikacji Microsoft Windows Forms itd.), mogą mieć negatywny wpływ na kod, ponieważ często dane są używane bezpośrednio jako parametry wywołania innego kodu.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-105">User data, which is any kind of input (data from a Web request or URL, input to controls of a Microsoft Windows Forms application, and so on), can adversely influence code because often that data is used directly as parameters to call other code.</span></span> <span data-ttu-id="7fd3c-106">Ta sytuacja jest analogiczna do złośliwego kodu wywołującego kod przy użyciu dziwnych parametrów i należy podjąć te same środki ostrożności.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-106">This situation is analogous to malicious code calling your code with strange parameters, and the same precautions should be taken.</span></span> <span data-ttu-id="7fd3c-107">Dane wejściowe użytkownika są naprawdę trudniejsze do zagwarantowania, ponieważ nie ma ramki stosu do śledzenia obecności potencjalnie niezaufanych danych.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-107">User input is actually harder to make safe because there is no stack frame to trace the presence of the potentially untrusted data.</span></span>

<span data-ttu-id="7fd3c-108">Znajdują się one wśród delikatnych i najtrudniejszych usterek związanych z bezpieczeństwem, które mogą znajdować się w kodzie, który wydaje się niezwiązany z zabezpieczeniami, są bramą do przekazywania nieprawidłowych danych do innego kodu.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-108">These are among the subtlest and hardest security bugs to find because, although they can exist in code that is seemingly unrelated to security, they are a gateway to pass bad data through to other code.</span></span> <span data-ttu-id="7fd3c-109">Aby wyszukać te błędy, postępuj zgodnie z dowolnym rodzajem danych wejściowych, Wyobraź sobie, jakie może być zakres możliwych wartości, i rozważ, czy kod, który widzi te dane, może obsłużyć wszystkie te przypadki.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-109">To look for these bugs, follow any kind of input data, imagine what the range of possible values might be, and consider whether the code seeing this data can handle all those cases.</span></span> <span data-ttu-id="7fd3c-110">Można naprawić te usterki poprzez sprawdzenie zakresu i odrzucenie wszelkich danych wejściowych, których kod nie może obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-110">You can fix these bugs through range checking and rejecting any input the code cannot handle.</span></span>

<span data-ttu-id="7fd3c-111">Poniżej wymieniono istotne zagadnienia dotyczące danych użytkownika:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-111">Some important considerations involving user data include the following:</span></span>

- <span data-ttu-id="7fd3c-112">Wszystkie dane użytkownika w odpowiedzi serwera są uruchamiane w kontekście lokacji serwera na kliencie programu.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-112">Any user data in a server response runs in the context of the server's site on the client.</span></span> <span data-ttu-id="7fd3c-113">Jeśli serwer sieci Web pobiera dane użytkownika i wstawia je do zwróconej strony sieci Web, może na przykład zawierać **\<script>** tag i działać jako Jeśli z serwera.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-113">If your Web server takes user data and inserts it into the returned Web page, it might, for example, include a **\<script>** tag and run as if from the server.</span></span>

- <span data-ttu-id="7fd3c-114">Należy pamiętać, że klient może zażądać dowolnego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-114">Remember that the client can request any URL.</span></span>

- <span data-ttu-id="7fd3c-115">Weź pod uwagę lewę lub nieprawidłowe ścieżki:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-115">Consider tricky or invalid paths:</span></span>

  - <span data-ttu-id="7fd3c-116">.. \, bardzo długie ścieżki.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-116">..\ , extremely long paths.</span></span>

  - <span data-ttu-id="7fd3c-117">Użycie znaków wieloznacznych (\*).</span><span class="sxs-lookup"><span data-stu-id="7fd3c-117">Use of wild card characters (\*).</span></span>

  - <span data-ttu-id="7fd3c-118">Rozszerzenie tokenu (% token%).</span><span class="sxs-lookup"><span data-stu-id="7fd3c-118">Token expansion (%token%).</span></span>

  - <span data-ttu-id="7fd3c-119">Nietypowe formy ścieżek o specjalnym znaczeniu.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-119">Strange forms of paths with special meaning.</span></span>

  - <span data-ttu-id="7fd3c-120">Alternatywne nazwy strumieni systemu plików, takie jak `filename::$DATA` .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-120">Alternate file system stream names such as `filename::$DATA`.</span></span>

  - <span data-ttu-id="7fd3c-121">Krótkie wersje plików, `longfi~1` na przykład `longfilename` .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-121">Short versions of file names such as `longfi~1` for `longfilename`.</span></span>

- <span data-ttu-id="7fd3c-122">Pamiętaj, że w ramach oceny (UserData) można wykonać dowolną czynność.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-122">Remember that Eval(userdata) can do anything.</span></span>

- <span data-ttu-id="7fd3c-123">Uważaj na późne wiązanie do nazwy zawierającej pewne dane użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-123">Be wary of late binding to a name that includes some user data.</span></span>

- <span data-ttu-id="7fd3c-124">W przypadku pracy z danymi w sieci Web należy wziąć pod uwagę różne formy ucieczki, takie jak:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-124">If you are dealing with Web data, consider the various forms of escapes that are permissible, including:</span></span>

  - <span data-ttu-id="7fd3c-125">Szesnastkowe znaki ucieczki (% nn).</span><span class="sxs-lookup"><span data-stu-id="7fd3c-125">Hexadecimal escapes (%nn).</span></span>

  - <span data-ttu-id="7fd3c-126">Ucieczki Unicode (% NNN).</span><span class="sxs-lookup"><span data-stu-id="7fd3c-126">Unicode escapes (%nnn).</span></span>

  - <span data-ttu-id="7fd3c-127">Nadlongowe sekwencje UTF-8 (% nn% nn).</span><span class="sxs-lookup"><span data-stu-id="7fd3c-127">Overlong UTF-8 escapes (%nn%nn).</span></span>

  - <span data-ttu-id="7fd3c-128">Podwójne ucieczki (% nn staną się% mmnn, gdzie% mm jest ucieczką dla "%").</span><span class="sxs-lookup"><span data-stu-id="7fd3c-128">Double escapes (%nn becomes %mmnn, where %mm is the escape for '%').</span></span>

- <span data-ttu-id="7fd3c-129">Należy ostrożnie wymusić nazwy użytkowników, które mogą mieć więcej niż jeden format kanoniczny.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-129">Be wary of user names that might have more than one canonical format.</span></span> <span data-ttu-id="7fd3c-130">Można na przykład użyć \\ formularza*username* lub formularza *username* @mydomain.example.com .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-130">For example, you can often use either the MYDOMAIN\\*username* form or the *username*@mydomain.example.com form.</span></span>

## <a name="see-also"></a><span data-ttu-id="7fd3c-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7fd3c-131">See also</span></span>

- [<span data-ttu-id="7fd3c-132">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="7fd3c-132">Secure Coding Guidelines</span></span>](secure-coding-guidelines.md)
