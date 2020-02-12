---
title: Jak wykryć, czy wtyczka .NET Framework 3.0 jest zainstalowana
ms.date: 03/30/2017
helpviewer_keywords:
- WinFX Runtime user-agent string
- presence of WPT [WPF], detecting
- detecting WPF presence [WPF]
ms.assetid: 7f71d652-1749-4379-945a-aa2e3994cb43
ms.openlocfilehash: 41010e615b6b3d10ebf6adc0e3f871873e94f409
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124458"
---
# <a name="how-to-detect-whether-the-net-framework-30-is-installed"></a><span data-ttu-id="45776-102">Jak wykryć, czy wtyczka .NET Framework 3.0 jest zainstalowana</span><span class="sxs-lookup"><span data-stu-id="45776-102">How to: Detect Whether the .NET Framework 3.0 Is Installed</span></span>
<span data-ttu-id="45776-103">Aby Administratorzy mogli wdrożyć aplikacje Microsoft .NET Framework w systemie, należy najpierw potwierdzić, że .NET Framework środowisko uruchomieniowe jest obecne.</span><span class="sxs-lookup"><span data-stu-id="45776-103">Before administrators can deploy Microsoft .NET Framework applications on a system, they must first confirm that the .NET Framework runtime is present.</span></span> <span data-ttu-id="45776-104">Ten temat zawiera skrypt zapisany w języku HTML/JavaScript, za pomocą którego Administratorzy mogą określić, czy .NET Framework jest obecny w systemie.</span><span class="sxs-lookup"><span data-stu-id="45776-104">This topic provides a script written in HTML/JavaScript that administrators can use to determine whether the .NET Framework is present on a system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="45776-105">Aby uzyskać bardziej szczegółowe informacje na temat instalowania, wdrażania i wykrywania platformy Microsoft .NET, zobacz Omówienie [wdrażania Microsoft .NET Framework w wersji 3,0](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480198(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="45776-105">For more detailed information on installing, deploying, and detecting the Microsoft .NET Framework, see the discussion in [Deploying Microsoft .NET Framework Version 3.0](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480198(v=msdn.10)).</span></span>  
  
<a name="content_expiration"></a>   
## <a name="detect-the-net-clr-user-agent-string"></a><span data-ttu-id="45776-106">Wykrywanie ciągu agenta użytkownika platformy .NET CLR</span><span class="sxs-lookup"><span data-stu-id="45776-106">Detect the ".NET CLR" User-Agent String</span></span>  
 <span data-ttu-id="45776-107">Po zainstalowaniu .NET Framework MSI dodaje ".NET CLR" i numer wersji do ciągu UserAgent.</span><span class="sxs-lookup"><span data-stu-id="45776-107">When .NET Framework is installed, the MSI adds ".NET CLR" and the version number to the UserAgent string.</span></span> <span data-ttu-id="45776-108">Poniższy przykład przedstawia skrypt osadzony na prostej stronie HTML.</span><span class="sxs-lookup"><span data-stu-id="45776-108">The following example shows a script embedded in a simple HTML page.</span></span> <span data-ttu-id="45776-109">Skrypt przeszukuje ciąg UserAgent, aby określić, czy .NET Framework jest zainstalowana, i wyświetla komunikat o stanie na wynikach wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="45776-109">The script searches the UserAgent string to determine whether .NET Framework is installed, and displays a status message on the results of the search.</span></span>  
  
```html  
<HTML>  
  <HEAD>  
    <TITLE>Test for the .NET Framework 3.0</TITLE>  
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />  
    <SCRIPT LANGUAGE="JavaScript">  
    <!--  
    var dotNETRuntimeVersion = "3.0.04425.00";  
  
    function window::onload()  
    {  
      if (HasRuntimeVersion(dotNETRuntimeVersion))  
      {  
        result.innerText =   
          "This machine has the correct version of the .NET Framework 3.0: "   
          + dotNETRuntimeVersion  
      }   
      else  
      {  
        result.innerText =   
          "This machine does not have the correct version of the .NET Framework 3.0."  
      }  
      result.innerText += "\n\nThis machine's userAgent string is: " +   
        navigator.userAgent + ".";  
    }  
  
    //  
    // Retrieve the version from the user agent string and   
    // compare with the specified version.  
    //  
    function HasRuntimeVersion(versionToCheck)  
    {  
      var userAgentString =   
        navigator.userAgent.match(/.NET CLR [0-9.]+/g);  
  
      if (userAgentString != null)  
      {  
        var i;  
  
        for (i = 0; i < userAgentString.length; ++i)  
        {  
          if (CompareVersions(GetVersion(versionToCheck),   
            GetVersion(userAgentString[i])) <= 0)  
            return true;  
        }  
      }  
  
      return false;  
    }  
  
    //  
    // Extract the numeric part of the version string.  
    //  
    function GetVersion(versionString)  
    {  
      var numericString =   
        versionString.match(/([0-9]+)\.([0-9]+)\.([0-9]+)/i);  
      return numericString.slice(1);  
    }  
  
    //  
    // Compare the 2 version strings by converting them to numeric format.  
    //  
    function CompareVersions(version1, version2)  
    {  
      for (i = 0; i < version1.length; ++i)  
      {  
        var number1 = new Number(version1[i]);  
        var number2 = new Number(version2[i]);  
  
        if (number1 < number2)  
          return -1;  
  
        if (number1 > number2)  
          return 1;  
      }  
  
      return 0;  
    }  
  
    -->  
    </SCRIPT>  
  </HEAD>  
  
  <BODY>  
    <div id="result" />  
  </BODY>  
</HTML>  
```  
  
 <span data-ttu-id="45776-110">Jeśli wyszukiwanie wersji środowiska .NET CLR powiedzie się, zostanie wyświetlony następujący typ komunikatu o stanie:</span><span class="sxs-lookup"><span data-stu-id="45776-110">If the search for the ".NET CLR " version is successful, the following type of status message appears:</span></span>  
  
 `This machine has the correct version of the .NET Framework 3.0: 3.0.04425.00`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727; .NET CLR 3.0.04425.00).`  
  
 <span data-ttu-id="45776-111">W przeciwnym razie zostanie wyświetlony następujący typ komunikatu o stanie:</span><span class="sxs-lookup"><span data-stu-id="45776-111">Otherwise, the following type of status message appears:</span></span>  
  
 `This machine does not have correct version of the .NET Framework 3.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727).`
