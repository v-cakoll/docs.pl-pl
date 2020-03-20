---
title: Narzędzie rejestracji modelu ServiceModel (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: a6f65ccc6caa0a7e496e7de8c83259ab48903753
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183109"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a>Narzędzie rejestracji modelu ServiceModel (ServiceModelReg.exe)
To narzędzie wiersza polecenia umożliwia zarządzanie rejestracją składników WCF i WF na jednym komputerze. W normalnych warunkach nie należy używać tego narzędzia, ponieważ składniki WCF i WF są konfigurowane po zainstalowaniu. Ale jeśli występują problemy z aktywacją usługi, możesz spróbować zarejestrować składniki za pomocą tego narzędzia.  
  
## <a name="syntax"></a>Składnia  
  
```console  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a>Uwagi  
 Narzędzie można znaleźć w następującej lokalizacji:  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\  
  
> [!NOTE]
> Po uruchomieniu narzędzia rejestracji ServiceModel w systemie Windows Vista okno dialogowe **Funkcje systemu Windows** może nie odzwierciedlać włączenia opcji **Aktywacja HTTP programu Windows Communication Foundation** w obszarze Microsoft **.NET Framework 3.0.** Dostęp do okna dialogowego **Funkcje systemu Windows** można uzyskać, klikając przycisk **Start**, a następnie kliknij przycisk **Uruchom,** a następnie wpisując **polecenie Opcjonalne elementy .**  
  
 W poniższych tabelach opisano opcje, których można używać z programem ServiceModelReg.exe.  
  
|Opcja|Opis|  
|------------|-----------------|  
|`-ia`|Instaluje wszystkie składniki WCF i WF.|  
|`-ua`|Odinstalowuje wszystkie składniki WCF i WF.|  
|`-r`|Naprawia wszystkie komponenty WCF i WF.|  
|`-i`|Instaluje składniki WCF i WF określone za pomocą –c.|  
|`-u`|Odinstalowuje składniki WCF i WF określone za pomocą –c.|  
|`-c`|Instaluje lub odinstalowuje składnik:<br /><br /> - httpnamespace - REZERWACJA OBSZARU NAZW HTTP<br />- tcpportsharing – usługa udostępniania portów TCP<br />- tcpactivation – usługa aktywacji TCP (nieobsługiwała w profilu klienta .NET 4)<br />- namedpipeactivation - Nazwana usługa aktywacji potoku (nieobsługiwała w profilu klienta .NET 4<br />- msmqactivation – usługa aktywacji USŁUGI MSMQ (nieobsługiwany w profilu klienta .NET 4<br />- etw - manifesty śledzenia zdarzeń ETW (Windows Vista lub nowsze)|  
|`-q`|Tryb cichy (tylko rejestrowanie błędów wyświetlania)|  
|`-v`|Tryb informacji pełnej.|  
|`-nologo`|Pomija przesłanie praw autorskich i banerów.|  
|`-?`|Wyświetla tekst pomocy|  
  
## <a name="fixing-the-fileloadexception-error"></a>Naprawianie błędu FileLoadException  
 Jeśli zainstalowano poprzednie wersje WCF na komputerze, `FileLoadFoundException` może pojawić się błąd po uruchomieniu servicemodelreg narzędzie do zarejestrowania nowej instalacji. Może się tak zdarzyć, nawet jeśli ręcznie usunięto pliki z poprzedniej instalacji, ale ustawienia machine.config pozostały nienaruszone.  
  
 Komunikat o błędzie jest podobny do następującego.  
  
```console  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 Z komunikatu o błędzie należy zauważyć, że zestaw System.ServiceModel w wersji 2.0.0.0 został zainstalowany przez wczesną wersję programu Customer Technology Preview (CTP). Bieżąca wersja zestawu System.ServiceModel zwolniony jest 3.0.0.0 zamiast. W związku z tym ten problem występuje, gdy chcesz zainstalować oficjalne wydanie WCF na komputerze, na którym zainstalowano wczesną wersję CTP WCF, ale nie całkowicie odinstalowano.  
  
 Program ServiceModelReg.exe nie może wyczyścić wcześniejszych wpisów wersji ani rejestrować wpisów nowej wersji. Jedynym obejściem jest ręczna edycja pliku machine.config. Możesz zlokalizować ten plik w następującej lokalizacji.  
  
```console  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config
```  
  
 Jeśli korzystasz z WCF na komputerze 64-bitowym, należy również edytować ten sam plik w tej lokalizacji.  
  
```console  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config
```  
  
 Znajdź wszystkie węzły XML w tym pliku, które odwołują się do "System.ServiceModel, Version=2.0.0.0", usuń je i wszystkie węzły podrzędne. Zapisz plik i ponownie uruchom program ServiceModelReg.exe rozwiązuje ten problem.  
  
## <a name="examples"></a>Przykłady  
 Poniższe przykłady pokazują, jak korzystać z najczęstszych opcji narzędzia ServiceModelReg.exe.  
  
```console  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
