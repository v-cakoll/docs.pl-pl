---
title: Jak wykryć, czy wtyczka .NET Framework 3.0 jest zainstalowana
ms.date: 03/30/2017
helpviewer_keywords:
- WinFX Runtime user-agent string
- presence of WPT [WPF], detecting
- detecting WPF presence [WPF]
ms.assetid: 7f71d652-1749-4379-945a-aa2e3994cb43
ms.openlocfilehash: 60868661df442849db3f5421f8ea33f790fd83fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187366"
---
# <a name="how-to-detect-whether-the-net-framework-30-is-installed"></a><span data-ttu-id="2e247-102">Jak wykryć, czy wtyczka .NET Framework 3.0 jest zainstalowana</span><span class="sxs-lookup"><span data-stu-id="2e247-102">How to: Detect Whether the .NET Framework 3.0 Is Installed</span></span>
<span data-ttu-id="2e247-103">Zanim administratorzy będą mogli wdrażać aplikacje platformy Microsoft .NET Framework w systemie, muszą najpierw potwierdzić, że środowisko uruchomieniowe programu .NET Framework jest obecne.</span><span class="sxs-lookup"><span data-stu-id="2e247-103">Before administrators can deploy Microsoft .NET Framework applications on a system, they must first confirm that the .NET Framework runtime is present.</span></span> <span data-ttu-id="2e247-104">W tym temacie przedstawiono skrypt napisany w języku HTML/JavaScript, którego administratorzy mogą używać do określenia, czy program .NET Framework jest obecny w systemie.</span><span class="sxs-lookup"><span data-stu-id="2e247-104">This topic provides a script written in HTML/JavaScript that administrators can use to determine whether the .NET Framework is present on a system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2e247-105">Aby uzyskać bardziej szczegółowe informacje dotyczące instalowania, wdrażania i wykrywania programu Microsoft .NET Framework, zobacz dyskusję na temat [wdrażania programu Microsoft .NET Framework w wersji 3.0](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480198(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="2e247-105">For more detailed information on installing, deploying, and detecting the Microsoft .NET Framework, see the discussion in [Deploying Microsoft .NET Framework Version 3.0](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480198(v=msdn.10)).</span></span>  
  
<a name="content_expiration"></a>
## <a name="detect-the-net-clr-user-agent-string"></a><span data-ttu-id="2e247-106">Wykrywanie ciągu agenta użytkownika ".NET CLR"</span><span class="sxs-lookup"><span data-stu-id="2e247-106">Detect the ".NET CLR" User-Agent String</span></span>  
 <span data-ttu-id="2e247-107">Po zainstalowaniu programu .NET Framework msi dodaje ".NET CLR" i numer wersji do ciągu UserAgent.</span><span class="sxs-lookup"><span data-stu-id="2e247-107">When .NET Framework is installed, the MSI adds ".NET CLR" and the version number to the UserAgent string.</span></span> <span data-ttu-id="2e247-108">W poniższym przykładzie przedstawiono skrypt osadzony na prostej stronie HTML.</span><span class="sxs-lookup"><span data-stu-id="2e247-108">The following example shows a script embedded in a simple HTML page.</span></span> <span data-ttu-id="2e247-109">Skrypt przeszukuje ciąg UserAgent, aby ustalić, czy program .NET Framework jest zainstalowany, i wyświetla komunikat o stanie wyników wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="2e247-109">The script searches the UserAgent string to determine whether .NET Framework is installed, and displays a status message on the results of the search.</span></span>  
  
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
  
 <span data-ttu-id="2e247-110">Jeśli wyszukiwanie wersji ".NET CLR" zakończy się pomyślnie, zostanie wyświetlony następujący typ komunikatu o stanie:</span><span class="sxs-lookup"><span data-stu-id="2e247-110">If the search for the ".NET CLR " version is successful, the following type of status message appears:</span></span>  
  
 `This machine has the correct version of the .NET Framework 3.0: 3.0.04425.00`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727; .NET CLR 3.0.04425.00).`  
  
 <span data-ttu-id="2e247-111">W przeciwnym razie zostanie wyświetlony następujący typ komunikatu o stanie:</span><span class="sxs-lookup"><span data-stu-id="2e247-111">Otherwise, the following type of status message appears:</span></span>  
  
 `This machine does not have correct version of the .NET Framework 3.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727).`
