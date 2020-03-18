---
title: Zabezpieczenia i dane użytkownika
description: Kod może przekazywać dane wprowadzone przez użytkownika jako parametry do innego kodu, co może mieć wpływ na bezpieczeństwo. Można wykonać sprawdzanie zakresu, aby odrzucić problematyczne dane wejściowe.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
ms.openlocfilehash: fa9f8d4708e928c51e446d8369c9b4556fc6fb77
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186104"
---
# <a name="security-and-user-input"></a><span data-ttu-id="25d20-104">Zabezpieczenia i dane użytkownika</span><span class="sxs-lookup"><span data-stu-id="25d20-104">Security and User Input</span></span>

<span data-ttu-id="25d20-105">Dane użytkownika, który jest wszelkiego rodzaju danych wejściowych (dane z żądania sieci Web lub adresu URL, dane wejściowe do formantów aplikacji Microsoft Windows Forms i tak dalej), może niekorzystnie wpływać na kod, ponieważ często te dane są używane bezpośrednio jako parametry do wywołania innego kodu.</span><span class="sxs-lookup"><span data-stu-id="25d20-105">User data, which is any kind of input (data from a Web request or URL, input to controls of a Microsoft Windows Forms application, and so on), can adversely influence code because often that data is used directly as parameters to call other code.</span></span> <span data-ttu-id="25d20-106">Ta sytuacja jest analogiczna do złośliwego kodu wywołującego kod z dziwnymi parametrami i należy podjąć te same środki ostrożności.</span><span class="sxs-lookup"><span data-stu-id="25d20-106">This situation is analogous to malicious code calling your code with strange parameters, and the same precautions should be taken.</span></span> <span data-ttu-id="25d20-107">Dane wejściowe użytkownika jest rzeczywiście trudniejsze do bezpiecznego, ponieważ nie ma ramki stosu do śledzenia obecności potencjalnie niezaufanych danych.</span><span class="sxs-lookup"><span data-stu-id="25d20-107">User input is actually harder to make safe because there is no stack frame to trace the presence of the potentially untrusted data.</span></span>

<span data-ttu-id="25d20-108">Są to jedne z najsubtelniejszych i najtrudniejszych błędów zabezpieczeń do znalezienia, ponieważ chociaż mogą istnieć w kodzie, który pozornie nie ma związku z zabezpieczeniami, są bramą do przekazywania złych danych do innego kodu.</span><span class="sxs-lookup"><span data-stu-id="25d20-108">These are among the subtlest and hardest security bugs to find because, although they can exist in code that is seemingly unrelated to security, they are a gateway to pass bad data through to other code.</span></span> <span data-ttu-id="25d20-109">Aby wyszukać te błędy, należy wykonać wszelkiego rodzaju danych wejściowych, wyobrazić sobie, jaki zakres możliwych wartości może być i zastanów się, czy kod widząc te dane może obsłużyć wszystkie te przypadki.</span><span class="sxs-lookup"><span data-stu-id="25d20-109">To look for these bugs, follow any kind of input data, imagine what the range of possible values might be, and consider whether the code seeing this data can handle all those cases.</span></span> <span data-ttu-id="25d20-110">Można naprawić te błędy poprzez sprawdzanie zakresu i odrzucanie wszelkich danych wejściowych kod nie może obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="25d20-110">You can fix these bugs through range checking and rejecting any input the code cannot handle.</span></span>

<span data-ttu-id="25d20-111">Oto kilka ważnych kwestii związanych z danymi użytkownika:</span><span class="sxs-lookup"><span data-stu-id="25d20-111">Some important considerations involving user data include the following:</span></span>

- <span data-ttu-id="25d20-112">Wszystkie dane użytkownika w odpowiedzi serwera są uruchamiane w kontekście lokacji serwera na kliencie.</span><span class="sxs-lookup"><span data-stu-id="25d20-112">Any user data in a server response runs in the context of the server's site on the client.</span></span> <span data-ttu-id="25d20-113">Jeśli serwer sieci Web pobiera dane użytkownika i wstawia je do zwróconej strony sieci Web, może na przykład zawierać \*\* \<skrypt>\*\* tagu i uruchamiać tak, jakby z serwera.</span><span class="sxs-lookup"><span data-stu-id="25d20-113">If your Web server takes user data and inserts it into the returned Web page, it might, for example, include a **\<script>** tag and run as if from the server.</span></span>

- <span data-ttu-id="25d20-114">Pamiętaj, że klient może zażądać dowolnego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="25d20-114">Remember that the client can request any URL.</span></span>

- <span data-ttu-id="25d20-115">Rozważ trudne lub nieprawidłowe ścieżki:</span><span class="sxs-lookup"><span data-stu-id="25d20-115">Consider tricky or invalid paths:</span></span>

  - <span data-ttu-id="25d20-116">.. \ , bardzo długie ścieżki.</span><span class="sxs-lookup"><span data-stu-id="25d20-116">..\ , extremely long paths.</span></span>

  - <span data-ttu-id="25d20-117">Użycie symboli wieloznacznych (\*).</span><span class="sxs-lookup"><span data-stu-id="25d20-117">Use of wild card characters (\*).</span></span>

  - <span data-ttu-id="25d20-118">Rozszerzanie tokenu (%token%).</span><span class="sxs-lookup"><span data-stu-id="25d20-118">Token expansion (%token%).</span></span>

  - <span data-ttu-id="25d20-119">Dziwne formy ścieżek o szczególnym znaczeniu.</span><span class="sxs-lookup"><span data-stu-id="25d20-119">Strange forms of paths with special meaning.</span></span>

  - <span data-ttu-id="25d20-120">Alternatywne nazwy strumienia `filename::$DATA`systemu plików, takie jak .</span><span class="sxs-lookup"><span data-stu-id="25d20-120">Alternate file system stream names such as `filename::$DATA`.</span></span>

  - <span data-ttu-id="25d20-121">Krótkie wersje nazw `longfi~1` plików, takie jak dla `longfilename`.</span><span class="sxs-lookup"><span data-stu-id="25d20-121">Short versions of file names such as `longfi~1` for `longfilename`.</span></span>

- <span data-ttu-id="25d20-122">Pamiętaj, że Eval (userdata) może zrobić wszystko.</span><span class="sxs-lookup"><span data-stu-id="25d20-122">Remember that Eval(userdata) can do anything.</span></span>

- <span data-ttu-id="25d20-123">Uważaj na późne powiązanie z nazwą, która zawiera pewne dane użytkownika.</span><span class="sxs-lookup"><span data-stu-id="25d20-123">Be wary of late binding to a name that includes some user data.</span></span>

- <span data-ttu-id="25d20-124">Jeśli masz do czynienia z danymi sieci Web, należy wziąć pod uwagę różne formy ucieczki, które są dopuszczalne, w tym:</span><span class="sxs-lookup"><span data-stu-id="25d20-124">If you are dealing with Web data, consider the various forms of escapes that are permissible, including:</span></span>

  - <span data-ttu-id="25d20-125">Szesnastkowa ucieczka (%nn).</span><span class="sxs-lookup"><span data-stu-id="25d20-125">Hexadecimal escapes (%nn).</span></span>

  - <span data-ttu-id="25d20-126">Unicode ucieka (%nnn).</span><span class="sxs-lookup"><span data-stu-id="25d20-126">Unicode escapes (%nnn).</span></span>

  - <span data-ttu-id="25d20-127">Overlong UTF-8 ucieka (%nn%nn).</span><span class="sxs-lookup"><span data-stu-id="25d20-127">Overlong UTF-8 escapes (%nn%nn).</span></span>

  - <span data-ttu-id="25d20-128">Podwójne ucieczki (%nn staje się %mmnn, gdzie %mm jest ucieczką dla '%').</span><span class="sxs-lookup"><span data-stu-id="25d20-128">Double escapes (%nn becomes %mmnn, where %mm is the escape for '%').</span></span>

- <span data-ttu-id="25d20-129">Uważaj na nazwy użytkowników, które mogą mieć więcej niż jeden format kanoniczny.</span><span class="sxs-lookup"><span data-stu-id="25d20-129">Be wary of user names that might have more than one canonical format.</span></span> <span data-ttu-id="25d20-130">Na przykład często można użyć formularza\\*nazwa użytkownika* MYDOMAIN lub formularza nazwy@mydomain.example.com *użytkownika.*</span><span class="sxs-lookup"><span data-stu-id="25d20-130">For example, you can often use either the MYDOMAIN\\*username* form or the *username*@mydomain.example.com form.</span></span>

## <a name="see-also"></a><span data-ttu-id="25d20-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="25d20-131">See also</span></span>

- [<span data-ttu-id="25d20-132">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="25d20-132">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
