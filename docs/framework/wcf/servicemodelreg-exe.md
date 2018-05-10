---
title: Narzędzie rejestracji modelu ServiceModel (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: 5fab1a356cd035ed006bfe90d713e179907e0137
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a>Narzędzie rejestracji modelu ServiceModel (ServiceModelReg.exe)
To narzędzie wiersza polecenia umożliwia zarządzanie rejestracją składników WCF i WF na jednym komputerze. W normalnych okolicznościach nie należy do tego narzędzia można użyć jako WCF i WF składniki są konfigurowane podczas instalacji. Ale jeśli masz problemy z aktywacją usługi, możesz zarejestrować składników za pomocą tego narzędzia.  
  
## <a name="syntax"></a>Składnia  
  
```  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a>Uwagi  
 Narzędzie można znaleźć w następującej lokalizacji:  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Foundation\ komunikacji  
  
> [!NOTE]
>  Po uruchomieniu narzędzia rejestracji modelu ServiceModel [!INCLUDE[wv](../../../includes/wv-md.md)], **funkcje systemu Windows** oknie dialogowym mogą nie uwzględniać który **Aktywacja HTTP programu Windows Communication Foundation** opcję w obszarze **Microsoft .NET Framework 3.0** jest włączona. **Funkcje systemu Windows** okna dialogowego można uzyskać, klikając **Start**, następnie kliknij przycisk **Uruchom** , a następnie wpisując **OptionalFeatures**.  
  
 W poniższych tabelach opisano opcje, które mogą być używane z ServiceModelReg.exe.  
  
|Opcja|Opis|  
|------------|-----------------|  
|`-ia`|Instaluje wszystkie składniki usługi WCF i WF.|  
|`-ua`|Odinstalowuje wszystkie składniki usługi WCF i WF.|  
|`-r`|Naprawia wszystkie składniki usługi WCF i WF.|  
|`-i`|Instaluje składniki usługi WCF i WF określony za pomocą – c.|  
|`-u`|Odinstalowuje składniki usługi WCF i WF określony za pomocą – c.|  
|`-c`|Instaluje lub odinstalowuje składnik:<br /><br /> -httpnamespace — Rezerwacja Namespace protokołu HTTP<br />Usługa udostępniania portów - tcpportsharing — TCP<br />Usługa aktywacji - tcpactivation — TCP (obsługiwane na .NET 4 Client Profile)<br />usługi - namedpipeactivation — nazwanego potoku aktywacji (obsługiwane na .NET 4 Client Profile<br />Usługa aktywacji - msmqactivation — MSMQ (obsługiwane na .NET 4 Client Profile<br />manifesty śledzenie zdarzeń — etw — ETW (system Windows Vista lub nowszy)|  
|`-q`|Tryb cichy (tylko rejestrowania błędów wyświetlania)|  
|`-v`|Tryb informacji pełnej.|  
|`-nologo`|Pomija komunikat o prawach autorskich oraz transparent.|  
|`-?`|Wyświetla Pomoc|  
  
## <a name="fixing-the-fileloadexception-error"></a>Naprawienie błędu fileloadexception —  
 Jeśli poprzednie wersje usług WCF jest zainstalowany na tym komputerze, mogą wystąpić `FileLoadFoundException` błąd podczas uruchamiania narzędzia ServiceModelReg można zarejestrować nowej instalacji. Może to nastąpić, nawet jeśli masz ręcznie usunąć pliki z poprzedniej instalacji, ale pozostanie bez zmian ustawień pliku machine.config.  
  
 Komunikat o błędzie jest podobny do następującego.  
  
```  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 Należy zauważyć, komunikat o błędzie do zainstalowania zestawu System.ServiceModel wersji 2.0.0.0 przez wczesnego wydawania klienta Technology Preview (CTP). Bieżąca wersja zestawu System.ServiceModel wydane jest 3.0.0.0 w zamian. Jeśli chcesz zainstalować oficjalnego wydania usługi WCF na komputerze, na którym wczesne wersji CTP programu WCF został zainstalowany, ale nie całkowicie odinstalowany w związku z tym napotkano ten problem.  
  
 ServiceModelReg.exe nie można wyczyścić wpisy wcześniejsze niż wersja, nie można zarejestrować nową wersję wpisów. Tylko obejście jest ręcznie edytować pliku machine.config. Możesz znaleźć tego pliku w następującej lokalizacji.  
  
```  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config   
```  
  
 Jeśli używasz usługi WCF na komputerze 64-bitowych, należy również edytować tego samego pliku w tej lokalizacji.  
  
```  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config   
```  
  
 Zlokalizuj żadnym węzłem XML w tym pliku, która odwołuje się do "System.ServiceModel, Version = 2.0.0.0", usuń je i węzły podrzędne. Zapisz plik i ponownie uruchom ServiceModelReg.exe rozwiązuje ten problem.  
  
## <a name="examples"></a>Przykłady  
 Następujące przykłady przedstawiają sposób użycia najczęściej używanych opcji narzędzia ServiceModelReg.exe.  
  
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
