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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce6dd2fcf913c16e4da68dec35ea3ccd8e90a948
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665783"
---
# <a name="security-and-user-input"></a><span data-ttu-id="1b924-102">Zabezpieczenia i dane użytkownika</span><span class="sxs-lookup"><span data-stu-id="1b924-102">Security and User Input</span></span>
<span data-ttu-id="1b924-103">Dane użytkownika, który jest dowolny rodzaj danych wejściowych z żądania sieci Web lub adresu URL, dane wejściowe do formantów w aplikacji Microsoft Windows Forms i tak dalej, mogą negatywnie wpłynąć na kod, ponieważ często używane dane bezpośrednio jako parametry, aby wywołać inny kod.</span><span class="sxs-lookup"><span data-stu-id="1b924-103">User data, which is any kind of input (data from a Web request or URL, input to controls of a Microsoft Windows Forms application, and so on), can adversely influence code because often that data is used directly as parameters to call other code.</span></span> <span data-ttu-id="1b924-104">Ta sytuacja jest odpowiednikiem złośliwego kodu, wywoływanie kodu z parametrami dziwne, a ten sam ostrożności.</span><span class="sxs-lookup"><span data-stu-id="1b924-104">This situation is analogous to malicious code calling your code with strange parameters, and the same precautions should be taken.</span></span> <span data-ttu-id="1b924-105">Dane wejściowe użytkownika jest faktycznie trudniejsze bezpieczne ponieważ nie ramek stosu śledzenia obecność potencjalnie niezaufanych danych.</span><span class="sxs-lookup"><span data-stu-id="1b924-105">User input is actually harder to make safe because there is no stack frame to trace the presence of the potentially untrusted data.</span></span>  
  
 <span data-ttu-id="1b924-106">Są wśród błędy subtlest i najtrudniejsze zabezpieczeń, aby znaleźć, ponieważ istnieją w kodzie, który jest pozornie związana z zabezpieczeniami, są one bramy do przekazania złe dane za pośrednictwem do innego kodu.</span><span class="sxs-lookup"><span data-stu-id="1b924-106">These are among the subtlest and hardest security bugs to find because, although they can exist in code that is seemingly unrelated to security, they are a gateway to pass bad data through to other code.</span></span> <span data-ttu-id="1b924-107">Aby znaleźć te błędy, postępuj zgodnie z dowolnego rodzaju danych wejściowych, Wyobraź sobie, co zakres możliwych wartości mogą być i należy wziąć pod uwagę, czy kod wyświetlania tych danych może obsługiwać wszystkich tych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="1b924-107">To look for these bugs, follow any kind of input data, imagine what the range of possible values might be, and consider whether the code seeing this data can handle all those cases.</span></span> <span data-ttu-id="1b924-108">Można naprawić te błędy w zakresie sprawdzania i odrzuca wszelkie wprowadzane, kod nie może obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="1b924-108">You can fix these bugs through range checking and rejecting any input the code cannot handle.</span></span>  
  
 <span data-ttu-id="1b924-109">Oto kilka istotnych kwestii dotyczących danych użytkownika:</span><span class="sxs-lookup"><span data-stu-id="1b924-109">Some important considerations involving user data include the following:</span></span>  
  
- <span data-ttu-id="1b924-110">Wszystkie dane użytkownika w odpowiedzi serwer działa w kontekście serwera lokacji na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="1b924-110">Any user data in a server response runs in the context of the server's site on the client.</span></span> <span data-ttu-id="1b924-111">Jeśli serwer sieci Web pobiera dane użytkownika i wstawia ją zwróconej stronie internetowej, na przykład może obejmować  **\<script >** tagu i uruchom tak, jakby z serwera.</span><span class="sxs-lookup"><span data-stu-id="1b924-111">If your Web server takes user data and inserts it into the returned Web page, it might, for example, include a **\<script>** tag and run as if from the server.</span></span>  
  
- <span data-ttu-id="1b924-112">Należy pamiętać, że klient może żądać dowolnego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="1b924-112">Remember that the client can request any URL.</span></span>  
  
- <span data-ttu-id="1b924-113">Należy wziąć pod uwagę trudne lub nieprawidłowe ścieżki:</span><span class="sxs-lookup"><span data-stu-id="1b924-113">Consider tricky or invalid paths:</span></span>  
  
    - <span data-ttu-id="1b924-114">.. \, bardzo długich ścieżek.</span><span class="sxs-lookup"><span data-stu-id="1b924-114">..\ , extremely long paths.</span></span>  
  
    - <span data-ttu-id="1b924-115">Użycie symboli wieloznacznych (\*).</span><span class="sxs-lookup"><span data-stu-id="1b924-115">Use of wild card characters (\*).</span></span>  
  
    - <span data-ttu-id="1b924-116">Rozszerzenie token (token %).</span><span class="sxs-lookup"><span data-stu-id="1b924-116">Token expansion (%token%).</span></span>  
  
    - <span data-ttu-id="1b924-117">Otrzymano nieoczekiwany rodzaje ścieżek przy użyciu specjalnego znaczenia.</span><span class="sxs-lookup"><span data-stu-id="1b924-117">Strange forms of paths with special meaning.</span></span>  
  
    - <span data-ttu-id="1b924-118">Alternatywne nazwy strumienia systemu plików, takich jak `filename::$DATA`.</span><span class="sxs-lookup"><span data-stu-id="1b924-118">Alternate file system stream names such as `filename::$DATA`.</span></span>  
  
    - <span data-ttu-id="1b924-119">Krótki wersje nazw plików, takich jak `longfi~1` dla `longfilename`.</span><span class="sxs-lookup"><span data-stu-id="1b924-119">Short versions of file names such as `longfi~1` for `longfilename`.</span></span>  
  
- <span data-ttu-id="1b924-120">Należy pamiętać, że Eval(userdata) można nic robić.</span><span class="sxs-lookup"><span data-stu-id="1b924-120">Remember that Eval(userdata) can do anything.</span></span>  
  
- <span data-ttu-id="1b924-121">Uważaj, późnego wiązania na nazwę, która zawiera dane użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1b924-121">Be wary of late binding to a name that includes some user data.</span></span>  
  
- <span data-ttu-id="1b924-122">Jeśli masz do czynienia z danych w sieci Web, należy wziąć pod uwagę różne rodzaje sekwencje ucieczki, które są dozwolone w tym:</span><span class="sxs-lookup"><span data-stu-id="1b924-122">If you are dealing with Web data, consider the various forms of escapes that are permissible, including:</span></span>  
  
    - <span data-ttu-id="1b924-123">Szesnastkowe sekwencje ucieczki (% nn).</span><span class="sxs-lookup"><span data-stu-id="1b924-123">Hexadecimal escapes (%nn).</span></span>  
  
    - <span data-ttu-id="1b924-124">Sekwencje ucieczki Unicode (% nnn).</span><span class="sxs-lookup"><span data-stu-id="1b924-124">Unicode escapes (%nnn).</span></span>  
  
    - <span data-ttu-id="1b924-125">Przedłużoną anuluje UTF-8 (% nn % nn).</span><span class="sxs-lookup"><span data-stu-id="1b924-125">Overlong UTF-8 escapes (%nn%nn).</span></span>  
  
    - <span data-ttu-id="1b924-126">Anuluje Double (% nn staje się mmnn %, gdzie % mm jest znak ucieczki "%").</span><span class="sxs-lookup"><span data-stu-id="1b924-126">Double escapes (%nn becomes %mmnn, where %mm is the escape for '%').</span></span>  
  
- <span data-ttu-id="1b924-127">Uważaj, nazw użytkowników, które może mieć więcej niż jeden kanoniczny format.</span><span class="sxs-lookup"><span data-stu-id="1b924-127">Be wary of user names that might have more than one canonical format.</span></span> <span data-ttu-id="1b924-128">Na przykład często używają obu moja_domena\\*username* formularza lub *username* @mydomain.example.com formularza.</span><span class="sxs-lookup"><span data-stu-id="1b924-128">For example, you can often use either the MYDOMAIN\\*username* form or the *username*@mydomain.example.com form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b924-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b924-129">See also</span></span>

- [<span data-ttu-id="1b924-130">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="1b924-130">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
