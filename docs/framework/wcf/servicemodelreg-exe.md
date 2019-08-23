---
title: Narzędzie rejestracji modelu ServiceModel (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: 519f303507ed873266cc05a7556073887b66ba6f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923028"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a>Narzędzie rejestracji modelu ServiceModel (ServiceModelReg.exe)
To narzędzie wiersza polecenia zapewnia możliwość zarządzania rejestracją składników WCF i WF na jednym komputerze. W normalnych okolicznościach nie należy używać tego narzędzia, ponieważ składniki WCF i WF są skonfigurowane podczas instalacji. Jeśli jednak występują problemy z aktywacją usługi, możesz spróbować zarejestrować składniki przy użyciu tego narzędzia.  
  
## <a name="syntax"></a>Składnia  
  
```  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a>Uwagi  
 Narzędzie można znaleźć w następującej lokalizacji:  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\  
  
> [!NOTE]
> Po uruchomieniu narzędzia rejestracji [!INCLUDE[wv](../../../includes/wv-md.md)]ServiceModel w systemie okno dialogowe **funkcji systemu Windows** może nie odzwierciedlać, że opcja **Windows Communication Foundation Aktywacja HTTP** w obszarze **Microsoft .NET Framework 3,0** jest włączona. Do okna dialogowego **funkcje systemu Windows** można uzyskać dostęp przez kliknięcie przycisku **Start**, a następnie kliknij pozycję **Uruchom** , a następnie wpisz **OptionalFeatures**.  
  
 W poniższych tabelach opisano opcje, których można użyć w programie ServiceModelReg. exe.  
  
|Opcja|Opis|  
|------------|-----------------|  
|`-ia`|Instaluje wszystkie składniki WCF i WF.|  
|`-ua`|Odinstalowuje wszystkie składniki WCF i WF.|  
|`-r`|Naprawia wszystkie składniki WCF i WF.|  
|`-i`|Instaluje składniki WCF i WF określone za pomocą parametru-c.|  
|`-u`|Odinstalowuje składniki WCF i WF określone za pomocą parametru-c.|  
|`-c`|Instaluje lub Odinstalowuje składnik:<br /><br /> -httpnamespace — rezerwacja przestrzeni nazw protokołu HTTP<br />-tcpportsharing — usługa udostępniania portów TCP<br />-tcpactivation — usługa aktywacji TCP (nieobsługiwana w profilu klienta .NET 4)<br />-namedpipeactivation — usługa aktywacji potoków nazwanych (nieobsługiwana w profilu klienta .NET 4<br />-Usługa MsmqActivation — usługa aktywacji usługi MSMQ (nieobsługiwana w profilu klienta .NET 4<br />-ETW — manifesty śledzenia zdarzeń ETW (system Windows Vista lub nowszy)|  
|`-q`|Tryb cichy (wyświetla tylko rejestrowanie błędów)|  
|`-v`|Tryb informacji pełnej.|  
|`-nologo`|Pomija informacje o prawach autorskich i baneru.|  
|`-?`|Wyświetla tekst pomocy|  
  
## <a name="fixing-the-fileloadexception-error"></a>Naprawianie błędu FileLoadException  
 Jeśli na komputerze zainstalowano poprzednie wersje programu WCF, podczas uruchamiania narzędzia ServiceModelReg `FileLoadFoundException` w celu zarejestrowania nowej instalacji może wystąpić błąd. Może się tak zdarzyć nawet w przypadku ręcznego usuwania plików z poprzedniej instalacji, ale pozostawionie ustawień Machine. config bez zmian.  
  
 Komunikat o błędzie jest podobny do poniższego.  
  
```  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 Należy zwrócić uwagę na komunikat o błędzie informujący o tym, że zestaw 2.0.0.0 w wersji System. ServiceModel został zainstalowany przez wczesną wersję zapoznawczą klienta (CTP). Bieżąca wersja zestawu System. ServiceModel wydano 3.0.0.0. W związku z tym ten problem występuje, gdy chcesz zainstalować oficjalną wersję programu WCF na komputerze, na którym zainstalowano wczesną wersję CTP programu WCF, ale nie została ona całkowicie odinstalowana.  
  
 ServiceModelReg. exe nie może oczyścić wcześniejszych wpisów wersji ani nie może zarejestrować wpisów nowej wersji. Jedyną obejściem jest ręczne edytowanie pliku Machine. config. Ten plik można zlokalizować w następującej lokalizacji.  
  
```  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config   
```  
  
 Jeśli używasz programu WCF na komputerze 64-bitowym, należy również edytować ten sam plik w tej lokalizacji.  
  
```  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config   
```  
  
 Zlokalizuj wszystkie węzły XML w tym pliku, które odwołują się do "System. ServiceModel, Version = 2.0.0.0", usuń je i wszystkie węzły podrzędne. Zapisz plik i ponownie uruchom ServiceModelReg. exe rozwiązuje ten problem.  
  
## <a name="examples"></a>Przykłady  
 W poniższych przykładach pokazano, jak używać najbardziej typowych opcji narzędzia ServiceModelReg. exe.  
  
```  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
