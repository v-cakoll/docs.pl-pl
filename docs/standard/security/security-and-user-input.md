---
title: Zabezpieczenia i dane użytkownika
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
caps.latest.revision: ''
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 157e20a80f0a76e157fad091bec6bfe635a9ccb8
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="security-and-user-input"></a><span data-ttu-id="8268e-102">Zabezpieczenia i dane użytkownika</span><span class="sxs-lookup"><span data-stu-id="8268e-102">Security and User Input</span></span>
<span data-ttu-id="8268e-103">Dane użytkownika, który jest dowolny rodzaj danych wejściowych (dane z żądania sieci Web lub adres URL, w danych wejściowych do formantów w aplikacji formularzy systemu Windows firmy Microsoft, i tak dalej), może negatywnie wpłynąć na kodu, ponieważ często używane dane bezpośrednio jako parametry, aby wywołać inny kod.</span><span class="sxs-lookup"><span data-stu-id="8268e-103">User data, which is any kind of input (data from a Web request or URL, input to controls of a Microsoft Windows Forms application, and so on), can adversely influence code because often that data is used directly as parameters to call other code.</span></span> <span data-ttu-id="8268e-104">Taka sytuacja jest odpowiednikiem złośliwego kodu wywoływanie kodu z parametrami dziwne, a sam ostrożności.</span><span class="sxs-lookup"><span data-stu-id="8268e-104">This situation is analogous to malicious code calling your code with strange parameters, and the same precautions should be taken.</span></span> <span data-ttu-id="8268e-105">Dane wejściowe użytkownika jest rzeczywiście trudniej upewnij bezpieczne, ponieważ nie istnieje żadne ramki stosu śledzenie obecności potencjalnie niezaufanych danych.</span><span class="sxs-lookup"><span data-stu-id="8268e-105">User input is actually harder to make safe because there is no stack frame to trace the presence of the potentially untrusted data.</span></span>  
  
 <span data-ttu-id="8268e-106">Są to między usterki subtlest i najtrudniejsze zabezpieczeń, aby dowiedzieć się, ponieważ istnieją w kodzie, który jest pozornie związana z zabezpieczeniami, są one bramy do przekazania złe dane za pośrednictwem do innego kodu.</span><span class="sxs-lookup"><span data-stu-id="8268e-106">These are among the subtlest and hardest security bugs to find because, although they can exist in code that is seemingly unrelated to security, they are a gateway to pass bad data through to other code.</span></span> <span data-ttu-id="8268e-107">Aby znaleźć te błędy, wykonaj dowolny rodzaj danych wejściowych, Wyobraź sobie co zakresu możliwych wartości może być i należy wziąć pod uwagę, czy kod wyświetlać te dane można obsługiwać wszystkich tych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="8268e-107">To look for these bugs, follow any kind of input data, imagine what the range of possible values might be, and consider whether the code seeing this data can handle all those cases.</span></span> <span data-ttu-id="8268e-108">Możesz rozwiązać te usterki w zakresie kontroli i odrzuca wszystkie wejściowy kod nie może obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="8268e-108">You can fix these bugs through range checking and rejecting any input the code cannot handle.</span></span>  
  
 <span data-ttu-id="8268e-109">Oto kilka istotnych kwestii dotyczących danych użytkownika:</span><span class="sxs-lookup"><span data-stu-id="8268e-109">Some important considerations involving user data include the following:</span></span>  
  
-   <span data-ttu-id="8268e-110">Wszystkie dane użytkownika w odpowiedzi serwer działa w kontekście serwera lokacji na kliencie.</span><span class="sxs-lookup"><span data-stu-id="8268e-110">Any user data in a server response runs in the context of the server's site on the client.</span></span> <span data-ttu-id="8268e-111">Jeśli serwer sieci Web pobiera dane użytkownika i wstawia go do zwróconej stronie sieci Web, na przykład może zawierać  **\<skryptu >** tagu i uruchom tak, jakby z serwera.</span><span class="sxs-lookup"><span data-stu-id="8268e-111">If your Web server takes user data and inserts it into the returned Web page, it might, for example, include a **\<script>** tag and run as if from the server.</span></span>  
  
-   <span data-ttu-id="8268e-112">Należy pamiętać, że klient może żądać dowolny adres URL.</span><span class="sxs-lookup"><span data-stu-id="8268e-112">Remember that the client can request any URL.</span></span>  
  
-   <span data-ttu-id="8268e-113">Należy wziąć pod uwagę ścieżek trudnych lub jest nieprawidłowy:</span><span class="sxs-lookup"><span data-stu-id="8268e-113">Consider tricky or invalid paths:</span></span>  
  
    -   <span data-ttu-id="8268e-114">.. \, bardzo długie ścieżki.</span><span class="sxs-lookup"><span data-stu-id="8268e-114">..\ , extremely long paths.</span></span>  
  
    -   <span data-ttu-id="8268e-115">Użycie symboli wieloznacznych (\*).</span><span class="sxs-lookup"><span data-stu-id="8268e-115">Use of wild card characters (\*).</span></span>  
  
    -   <span data-ttu-id="8268e-116">Rozszerzenia token (token %).</span><span class="sxs-lookup"><span data-stu-id="8268e-116">Token expansion (%token%).</span></span>  
  
    -   <span data-ttu-id="8268e-117">Formularze dziwne ścieżek o specjalnym znaczeniu.</span><span class="sxs-lookup"><span data-stu-id="8268e-117">Strange forms of paths with special meaning.</span></span>  
  
    -   <span data-ttu-id="8268e-118">Alternatywne nazwy strumienia systemu plików, takich jak `filename::$DATA`.</span><span class="sxs-lookup"><span data-stu-id="8268e-118">Alternate file system stream names such as `filename::$DATA`.</span></span>  
  
    -   <span data-ttu-id="8268e-119">Krótka wersji nazw plików, takich jak `longfi~1` dla `longfilename`.</span><span class="sxs-lookup"><span data-stu-id="8268e-119">Short versions of file names such as `longfi~1` for `longfilename`.</span></span>  
  
-   <span data-ttu-id="8268e-120">Należy pamiętać, że Eval(userdata) mogą wykonywać żadnych czynności.</span><span class="sxs-lookup"><span data-stu-id="8268e-120">Remember that Eval(userdata) can do anything.</span></span>  
  
-   <span data-ttu-id="8268e-121">Uważaj, późnego wiązania na nazwę, która zawiera niektóre dane użytkowników.</span><span class="sxs-lookup"><span data-stu-id="8268e-121">Be wary of late binding to a name that includes some user data.</span></span>  
  
-   <span data-ttu-id="8268e-122">Jeśli mamy do czynienia z danych w sieci Web, należy wziąć pod uwagę różne rodzaje specjalne, które są dopuszczalne, w tym:</span><span class="sxs-lookup"><span data-stu-id="8268e-122">If you are dealing with Web data, consider the various forms of escapes that are permissible, including:</span></span>  
  
    -   <span data-ttu-id="8268e-123">Wyprowadza szesnastkowym (% nn).</span><span class="sxs-lookup"><span data-stu-id="8268e-123">Hexadecimal escapes (%nn).</span></span>  
  
    -   <span data-ttu-id="8268e-124">Specjalne Unicode (% nnn).</span><span class="sxs-lookup"><span data-stu-id="8268e-124">Unicode escapes (%nnn).</span></span>  
  
    -   <span data-ttu-id="8268e-125">Przedłużoną specjalne UTF-8 (% nn % nn).</span><span class="sxs-lookup"><span data-stu-id="8268e-125">Overlong UTF-8 escapes (%nn%nn).</span></span>  
  
    -   <span data-ttu-id="8268e-126">Wyprowadza Double (% nn staje się mmnn %, gdzie % mm jest ucieczki "%").</span><span class="sxs-lookup"><span data-stu-id="8268e-126">Double escapes (%nn becomes %mmnn, where %mm is the escape for '%').</span></span>  
  
-   <span data-ttu-id="8268e-127">Uważaj, nazw użytkowników, które mogą mieć więcej niż jeden format kanoniczny.</span><span class="sxs-lookup"><span data-stu-id="8268e-127">Be wary of user names that might have more than one canonical format.</span></span> <span data-ttu-id="8268e-128">Na przykład często służą albo moja_domena\\*username* formularza lub *username* @mydomain.example.com formularza.</span><span class="sxs-lookup"><span data-stu-id="8268e-128">For example, you can often use either the MYDOMAIN\\*username* form or the *username*@mydomain.example.com form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8268e-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8268e-129">See Also</span></span>  
 [<span data-ttu-id="8268e-130">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="8268e-130">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
