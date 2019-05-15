---
title: 'Instrukcje: Wykrywanie, czy wtyczka .NET Framework 3.5 jest zainstalowana'
ms.date: 03/30/2017
helpviewer_keywords:
- verifying whether.NET Framework 3.5 is installed [WPF]
- detecting .NET Framework 3.5 installation [WPF]
- detecting whether.NET Framework 3.5 is installed [WPF]
- determining whether.NET Framework 3.5 is installed [WPF]
ms.assetid: 8556a9d2-1eb8-48ef-919c-5baf22a2a9a2
ms.openlocfilehash: 7c373d9fd5934be98735cd814dafb35ed81fddfe
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592627"
---
# <a name="how-to-detect-whether-the-net-framework-35-is-installed"></a><span data-ttu-id="45e5a-102">Instrukcje: Wykrywanie, czy wtyczka .NET Framework 3.5 jest zainstalowana</span><span class="sxs-lookup"><span data-stu-id="45e5a-102">How to: Detect Whether the .NET Framework 3.5 Is Installed</span></span>
<span data-ttu-id="45e5a-103">Zanim administratorzy mogą wdrażać aplikacje Windows Presentation Foundation (WPF) w systemie, który jest przeznaczony dla [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], ich musi najpierw potwierdzić, że [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] środowiska uruchomieniowego jest obecny.</span><span class="sxs-lookup"><span data-stu-id="45e5a-103">Before administrators can deploy Windows Presentation Foundation (WPF) applications on a system that targets the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], they must first confirm that the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] runtime is present.</span></span> <span data-ttu-id="45e5a-104">Ten temat zawiera skrypt napisany w języku HTML/JavaScript, Administratorzy mogą używać do określenia czy [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] znajduje się w systemie.</span><span class="sxs-lookup"><span data-stu-id="45e5a-104">This topic provides a script written in HTML/JavaScript that administrators can use to determine whether the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] is present on a system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45e5a-105">Aby uzyskać szczegółowe informacje na temat instalowania, wdrażanie i wykrywanie programu .NET Framework, zobacz [Instalowanie programu .NET Framework dla deweloperów](../../install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="45e5a-105">For more detailed information on installing, deploying, and detecting the .NET Framework, see [Install the .NET Framework for developers](../../install/guide-for-developers.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="45e5a-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="45e5a-106">Example</span></span>  
 <span data-ttu-id="45e5a-107">Gdy [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] jest zainstalowany, MSI dodaje ".NET CLR" oraz numer wersji do ciąg agenta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="45e5a-107">When the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] is installed, the MSI adds ".NET CLR" and the version number to the UserAgent string.</span></span> <span data-ttu-id="45e5a-108">Poniższy przykład pokazuje skrypt osadzone w prostą stronę HTML.</span><span class="sxs-lookup"><span data-stu-id="45e5a-108">The following example shows a script embedded in a simple HTML page.</span></span> <span data-ttu-id="45e5a-109">Skrypt wyszukuje ciąg agenta użytkownika, aby określić, czy [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] jest zainstalowany i wyświetla komunikat o stanie na wyniki wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="45e5a-109">The script searches the UserAgent string to determine whether the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] is installed, and displays a status message on the results of the search.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45e5a-110">Ten skrypt jest przeznaczony dla programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="45e5a-110">This script is designed for Internet Explorer.</span></span> <span data-ttu-id="45e5a-111">Inne przeglądarki nie może zawierać informacje o .NET CLR w ciąg agenta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="45e5a-111">Other browsers may not include .NET CLR information in the UserAgent string.</span></span>  
  
```  
<HTML>  
  <HEAD>  
    <TITLE>Test for the .NET Framework 3.5</TITLE>  
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />  
    <SCRIPT LANGUAGE="JavaScript">  
    <!--  
    var dotNETRuntimeVersion = "3.5.0.0";  
  
    function window::onload()  
    {  
      if (HasRuntimeVersion(dotNETRuntimeVersion))  
      {  
        result.innerText =   
          "This machine has the correct version of the .NET Framework 3.5."  
      }   
      else  
      {  
        result.innerText =   
          "This machine does not have the correct version of the .NET Framework 3.5." +  
          " The required version is v" + dotNETRuntimeVersion + ".";  
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
  
 <span data-ttu-id="45e5a-112">Jeśli wyszukiwania dla wersji ".NET CLR" zakończy się pomyślnie, zostanie wyświetlony następujący typ komunikatu o stanie:</span><span class="sxs-lookup"><span data-stu-id="45e5a-112">If the search for the ".NET CLR " version is successful, the following type of status message appears:</span></span>  
  
 `This machine has the correct version of the .NET Framework 3.5.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; .NET CLR 3.5.20726; MS-RTC LM 8).`  
  
 <span data-ttu-id="45e5a-113">W przeciwnym razie zostanie wyświetlony następujący typ komunikatu o stanie:</span><span class="sxs-lookup"><span data-stu-id="45e5a-113">Otherwise, the following type of status message appears:</span></span>  
  
 `This machine does not have the correct version of the .NET Framework 3.5. The required version is v3.5.0.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; MS-RTC LM 8).`  
  
## <a name="see-also"></a><span data-ttu-id="45e5a-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45e5a-114">See also</span></span>

- [<span data-ttu-id="45e5a-115">Wykrywanie, czy wtyczka .NET Framework 3.0 jest zainstalowana</span><span class="sxs-lookup"><span data-stu-id="45e5a-115">Detect Whether the .NET Framework 3.0 Is Installed</span></span>](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
