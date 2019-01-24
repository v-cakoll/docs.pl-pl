---
title: 'Instrukcje: Wykryj, czy zainstalowano programu .NET Framework 3.5'
ms.date: 03/30/2017
helpviewer_keywords:
- verifying whether.NET Framework 3.5 is installed [WPF]
- detecting .NET Framework 3.5 installation [WPF]
- detecting whether.NET Framework 3.5 is installed [WPF]
- determining whether.NET Framework 3.5 is installed [WPF]
ms.assetid: 8556a9d2-1eb8-48ef-919c-5baf22a2a9a2
ms.openlocfilehash: cbdac46a52ae92ec7a8f6fb819a3da54ddccce7b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636426"
---
# <a name="how-to-detect-whether-the-net-framework-35-is-installed"></a>Instrukcje: Wykryj, czy zainstalowano programu .NET Framework 3.5
Zanim administratorzy mogą wdrażać aplikacje Windows Presentation Foundation (WPF) w systemie, który jest przeznaczony dla [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], ich musi najpierw potwierdzić, że [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] środowiska uruchomieniowego jest obecny. Ten temat zawiera skrypt napisany w języku HTML/JavaScript, Administratorzy mogą używać do określenia czy [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] znajduje się w systemie.  
  
> [!NOTE]
>  Aby uzyskać szczegółowe informacje na temat instalowania, wdrażanie i wykrywanie [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], zobacz [Instalowanie programu .NET Framework dla deweloperów](../../../../docs/framework/install/guide-for-developers.md).  
  
## <a name="example"></a>Przykład  
 Gdy [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] jest zainstalowany, MSI dodaje ".NET CLR" oraz numer wersji do ciąg agenta użytkownika. Poniższy przykład pokazuje skrypt osadzone w prostą stronę HTML. Skrypt wyszukuje ciąg agenta użytkownika, aby określić, czy [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] jest zainstalowany i wyświetla komunikat o stanie na wyniki wyszukiwania.  
  
> [!NOTE]
>  Ten skrypt jest przeznaczony dla programu Internet Explorer. Inne przeglądarki nie może zawierać informacje o .NET CLR w ciąg agenta użytkownika.  
  
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
  
 Jeśli wyszukiwania dla wersji ".NET CLR" zakończy się pomyślnie, zostanie wyświetlony następujący typ komunikatu o stanie:  
  
 `This machine has the correct version of the .NET Framework 3.5.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; .NET CLR 3.5.20726; MS-RTC LM 8).`  
  
 W przeciwnym razie zostanie wyświetlony następujący typ komunikatu o stanie:  
  
 `This machine does not have the correct version of the .NET Framework 3.5. The required version is v3.5.0.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; MS-RTC LM 8).`  
  
## <a name="see-also"></a>Zobacz także
- [Wykrywanie, czy wtyczka .NET Framework 3.0 jest zainstalowana](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md)
