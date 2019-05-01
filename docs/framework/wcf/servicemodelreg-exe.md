---
title: Narzędzie rejestracji modelu ServiceModel (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: 5fab1a356cd035ed006bfe90d713e179907e0137
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051796"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a>Narzędzie rejestracji modelu ServiceModel (ServiceModelReg.exe)
To narzędzie wiersza polecenia umożliwia zarządzanie rejestracją programu WCF i WF składników na jednym komputerze. W normalnych warunkach nie należy do tego narzędzia można używać jako usługi WCF i WF składniki są konfigurowane podczas instalacji. Ale jeśli występują problemy z aktywacji usługi, możesz spróbować by zarejestrować komponenty za pomocą tego narzędzia.  
  
## <a name="syntax"></a>Składnia  
  
```  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a>Uwagi  
 Narzędzie można znaleźć w następującej lokalizacji:  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\  
  
> [!NOTE]
>  Po uruchomieniu narzędzie rejestracji modelu ServiceModel [!INCLUDE[wv](../../../includes/wv-md.md)], **funkcji Windows** oknie dialogowym mogą nie odzwierciedlać, **Aktywacja HTTP programu Windows Communication Foundation** opcję w obszarze **Microsoft .NET Framework 3.0** jest włączona. **Funkcji Windows** okno dialogowe jest możliwy, klikając **Start**, następnie kliknij przycisk **Uruchom** , a następnie wpisując **OptionalFeatures**.  
  
 W poniższych tabelach opisano opcje, które mogą być używane z ServiceModelReg.exe.  
  
|Opcja|Opis|  
|------------|-----------------|  
|`-ia`|Instaluje wszystkie składniki programu WCF i WF.|  
|`-ua`|Odinstalowuje wszystkie składniki programu WCF i WF.|  
|`-r`|Naprawia wszystkie składniki programu WCF i WF.|  
|`-i`|Instaluje składniki usługi WCF i WF określony za pomocą – c.|  
|`-u`|Odinstalowuje program WCF i WF składniki określony za pomocą – c.|  
|`-c`|Instaluje lub odinstalowuje składnik:<br /><br /> -httpnamespace — rezerwacji Namespace HTTP<br />współużytkowania portów - tcpportsharing — TCP<br />Usługa aktywacji - tcpactivation — TCP (nieobsługiwane w .NET 4 Client Profile)<br />usługi - namedpipeactivation — Aktywacja potoku nazwanego (nieobsługiwane w .NET 4 Client Profile<br />Usługa aktywacji - msmqactivation — MSMQ (nieobsługiwane w .NET 4 Client Profile<br />manifestów śledzenie zdarzeń — etw — zdarzeń systemu Windows (Windows Vista lub nowszy)|  
|`-q`|Tryb cichy (tylko rejestrowanie błędów display)|  
|`-v`|Tryb informacji pełnej.|  
|`-nologo`|Pomija komunikat o prawach autorskich i baneru.|  
|`-?`|Wyświetla tekst pomocy|  
  
## <a name="fixing-the-fileloadexception-error"></a>Naprawianie błędów fileloadexception —  
 Jeśli w poprzednich wersjach programu WCF jest zainstalowany na komputerze, może wystąpić `FileLoadFoundException` błąd podczas uruchamiania narzędzia ServiceModelReg do zarejestrowania nowej instalacji. Można to zrobić, nawet jeśli zajmujesz się ręcznie usunąć pliki z poprzedniej instalacji, ale ustawienia w pliku machine.config pozostają niezmienione.  
  
 Komunikat o błędzie jest podobny do następującego.  
  
```  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 Należy zauważyć, z komunikatu o błędzie zainstalowanie zestawu System.ServiceModel wersji 2.0.0.0 lub nowszej, to wczesna wersja Customer Technology Preview (CTP). Bieżąca wersja zestawu System.ServiceModel wydania jest 3.0.0.0 zamiast tego. W związku z tym ten problem występuje, jeśli chcesz zainstalować oficjalnego wydania usługi WCF na komputerze, gdzie to wczesna wersja CTP programu WCF została zainstalowana, ale nie jest całkowicie odinstalowany.  
  
 ServiceModelReg.exe nie można wyczyścić wpisów z poprzedniej wersji, nie można zarejestrować nową wersję wpisów. Jedynym obejściem jest ręczna Edycja pliku machine.config. Można zlokalizować ten plik w następującej lokalizacji.  
  
```  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config   
```  
  
 Jeśli używasz programu WCF na komputerze 64-bitowym, możesz również edytować tego samego pliku, w tym miejscu.  
  
```  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config   
```  
  
 Znajdź żadnym węzłem XML w tym pliku, który odwołuje się do "System.ServiceModel, Version = 2.0.0.0", usuń je i wszystkie węzły podrzędne. Zapisz plik i ponownie uruchom ServiceModelReg.exe rozwiązuje ten problem.  
  
## <a name="examples"></a>Przykłady  
 Poniższe przykłady pokazują, jak korzystać z najbardziej typowych opcji narzędzia ServiceModelReg.exe.  
  
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
