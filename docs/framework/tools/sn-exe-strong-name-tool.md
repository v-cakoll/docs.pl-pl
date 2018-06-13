---
title: Sn.exe (Narzędzie silnych nazw)
ms.date: 03/30/2017
helpviewer_keywords:
- public keys, signing files
- Strong Name tool
- Sn.exe
- assemblies [.NET Framework], signing
- signing files
- strong-named assemblies, signing files
- key pairs for signing files
ms.assetid: c1d2b532-1b8e-4c7a-8ac5-53b801135ec6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7e58d14eb29939ea1b91b5bdb75f691f5233d8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401124"
---
# <a name="snexe-strong-name-tool"></a>Sn.exe (Narzędzie silnych nazw)
Narzędzie Strong Name (Sn.exe) ułatwia zestawy logowania za pomocą [silnych nazw](../../../docs/framework/app-domains/strong-named-assemblies.md). Sn.exe dostarcza opcje do zarządzania kluczami, generowania podpisów i ich weryfikacji.  
  
 Aby uzyskać więcej informacji na silne nazwy i zestawy o silnych nazwach, zobacz [zestawy Strong-Named](../../../docs/framework/app-domains/strong-named-assemblies.md) i [porady: podpisać zestaw o silnej nazwie](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
 Narzędzie silnych nazw jest automatycznie instalowane z Visual Studio. Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera (lub wiersz polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
> [!NOTE]
>  Na komputerach 64-bitowych należy uruchomić 32-bitowej wersji Sn.exe przy użyciu wiersza polecenia programu Visual Studio i 64-bitowej wersji przy użyciu wiersza polecenia programu Visual Studio x64 Win64.  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
sn [-quiet][option [parameter(s)]]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Opcja|Opis|  
|------------|-----------------|  
|**-** *identityKeyPairFile* *signaturePublicKeyFile*|Generuje <xref:System.Reflection.AssemblySignatureKeyAttribute> migrować klucz tożsamości do klucza podpisu z pliku danych.|  
|**-ac** *identityPublicKeyFile* *identityKeyPairContainer* *signaturePublicKeyFile*|Generuje <xref:System.Reflection.AssemblySignatureKeyAttribute> migrować klucz tożsamości do klucza podpisu z kontenera kluczy danych.|  
|**-c** [*dostawcy usług kryptograficznych*]|Określa domyślnego dostawcę usług kryptograficznych (CSP) do podpisywania silnymi nazwami. To ustawienie odnosi się do całego komputera. Jeśli nie określisz nazwy CSP, Sn.exe wyczyści bieżące ustawienie.|  
|**-d** *kontenera*|Usuwa określony kontener kluczy z CSP silnej nazwy.|  
|**-D***assembly2 zestaw1* |Weryfikuje, czy dwa zestawy różnią się tylko podpisem. Jest to często używane jako sprawdzenie po ponownym podpisaniu zestawu inną parą kluczy.|  
|**-e***outfile zestawu* |Wyodrębnia klucza publicznego z *zestawu* i przechowuje ją w *outfile.*|  
|**-h**|Wyświetla składnię polecenia i opcje narzędzia.|  
|**-i** *PlikWejściowy kontenera*|Instaluje pary kluczy z *PlikWejściowy* w określonym kontenerze klucza. Kontener kluczy mieści się w CSP silnej nazwy.|  
|**-k** [*keysize*] *outfile*|Generuje nowy <xref:System.Security.Cryptography.RSACryptoServiceProvider> klucza o określonym rozmiarze i zapisuje go do określonego pliku.  Oba klucze, publiczny i prywatny, są zapisywane do pliku.<br /><br /> Jeśli nie określono rozmiaru klucza, w przypadku gdy zainstalowany jest ulepszony dostawca kryptograficzny firmy Microsoft, domyślnie generowany jest 1024-bitowy klucz; w przeciwnym wypadku, generowany jest 512-bitowy klucz.<br /><br /> *Keysize* parametru obsługuje długości kluczy z 384 bitów do 16 384 bitów w przyrostach 8 bitów, jeśli masz rozszerzony dostawca usług kryptograficznych Microsoft zainstalowane.  Obsługuje on długości kluczy od 384 bitów do 512 bitów rosnąco co 8 bitów, jeśli zainstalowany jest podstawowy dostawca kryptograficzny firmy Microsoft.|  
|**-m** [**y** *&#124;* **n**]|Określa, czy kontenery kluczy są specyficzne dla komputera, czy dla użytkownika. Jeśli określisz *y*, kontenerów kluczy są specyficzne dla komputera. Jeśli określisz *n*, kontenerów kluczy są specyficzne dla użytkownika.<br /><br /> Jeśli nie podano ani y ani n, ta opcja wyświetla bieżące ustawienie.|  
|**-o***PlikWejściowy* [*outfile*]  |Wyodrębnia klucza publicznego z *PlikWejściowy* i zapisuje go w pliku CSV. Poszczególne bajty klucza publicznego są rozdzielone przecinkami. Ten format jest użyteczny dla trwale zakodowanych odwołań do kluczy, takich jak zainicjowane tablice w kodzie źródłowym. Jeśli nie określisz *outfile*, ta opcja umieszcza dane wyjściowe w Schowku. **Uwaga:** ta opcja sprawdza, czy dane wejściowe jest tylko klucz publiczny. Jeśli `infile` zawiera pary kluczy z kluczem prywatnym, również jest wyodrębniany klucza prywatnego.|  
|**-p** *outfile PlikWejściowy* [*algorytm_mieszania*]|Wyodrębnia klucza publicznego z pary kluczy w *PlikWejściowy* i przechowuje ją w *outfile*, opcjonalnie przy użyciu algorytmu RSA, określony przez *algorytm_mieszania*. Ten klucz publiczny może być używany do opóźnione podpisywanie zestawu za pomocą **/delaysign+** i **/KeyFile** opcje [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Gdy zestaw jest podpisany z opóźnieniem, w czasie kompilacji ustawiany jest tylko klucz publiczny i rezerwowana jest przestrzeń w pliku na późniejsze dodanie podpisu, gdy znany będzie klucz prywatny.|  
|**-pc***kontenera* *outfile* [*algorytm_mieszania*]  |Wyodrębnia klucza publicznego z pary kluczy w *kontenera* i przechowuje ją w *outfile*. Jeśli używasz *algorytm_mieszania* opcji algorytmu RSA jest używany do wyodrębniania klucza publicznego.|  
|**-Pb** [**y** *&#124;* **n**]|Określa, czy wymuszona jest zasada obejścia silnej nazwy. Jeśli określisz *y*, silnej nazwy dla pełnego zaufania zestawy nie są weryfikowane podczas ładowania do pełnego zaufania <xref:System.AppDomain>. Jeśli określisz *n*, silnych nazw są weryfikowane pod kątem poprawności, ale nie dla określonej silnej nazwy. <xref:System.Security.Permissions.StrongNameIdentityPermission> Nie ma wpływu na zestawy pełnego zaufania. Musisz wykonać swoje własne sprawdzenie dopasowania silnej nazwy.<br /><br /> Jeśli żadna `y` ani `n` jest określony, ta opcja powoduje wyświetlenie bieżącego ustawienia. Wartość domyślna to `y`. **Uwaga:** na komputerach 64-bitowych, należy ustawić w 32-bitowej i 64-bitowych wystąpienia Sn.exe tego parametru.|  
|**-q**[**uiet**]|Określa tryb cichy; pomija wyświetlanie komunikatów o powodzeniu.|  
|**-R**[**a**] *zestawu* *PlikWejściowy*|Ponownie podpisuje wcześniej podpisanego lub podpisywany z opóźnieniem zestawu z pary kluczy w *PlikWejściowy*.<br /><br /> Jeśli **-Ra** jest używana, skróty są przeliczane dla wszystkich plików w zestawie.|  
|**Rc —**[**a**] *kontenera zestawu*|Ponownie podpisuje wcześniej podpisanego lub podpisywany z opóźnieniem zestawu z pary kluczy w *kontenera*.<br /><br /> Jeśli **- Rca** jest używana, skróty są przeliczane dla wszystkich plików w zestawie.|  
|**-Rh** *zestawu*|Oblicza ponownie skróty dla wszystkich plików w zestawie.|  
|**-t**[**p**] *PlikWejściowy*|Wyświetla tokenu klucza publicznego przechowywane w *PlikWejściowy*. Zawartość *PlikWejściowy* musi być wcześniej generowane na podstawie pliku pary kluczy przy użyciu klucza publicznego **-p**.  Nie używaj **-t [p]** opcję, aby wyodrębnić token bezpośrednio z pliku pary kluczy.<br /><br /> Sn.exe oblicza token przy użyciu funkcji skrótu z klucza publicznego. Aby zaoszczędzić przestrzeń, środowisko uruchomieniowe języka wspólnego zapisuje tokeny klucza publicznego w manifeście jako część odwołania do innego zestawu, gdy rejestruje zależność do zestawu z silną nazwą. **- Tp** opcja powoduje wyświetlenie klucza publicznego, oprócz tokenu. Jeśli <xref:System.Reflection.AssemblySignatureKeyAttribute> zastosowano atrybut do zestawu, token jest klucza tożsamości i jest wyświetlana nazwa algorytmu wyznaczania wartości skrótu i klucza tożsamości.<br /><br /> Zauważ, że ta opcja nie weryfikuje podpisu zestawu i nie powinna być używana do podejmowania decyzji dotyczących zaufania.  Ta opcja wyświetla jedynie surowe dane tokenu klucza publicznego.|  
|**-T**[**p**] *zestawu*|Wyświetla token klucza publicznego dla *zestawu.* *Zestawu* musi być nazwą pliku, który zawiera manifest zestawu.<br /><br /> Sn.exe oblicza token przy użyciu funkcji skrótu z klucza publicznego. Aby zaoszczędzić przestrzeń, środowisko uruchomieniowe przechowuje tokeny klucza publicznego w manifeście jako część odwołania do innego zestawu, gdy rejestruje zależność do zestawu z silną nazwą. **- Tp** opcja powoduje wyświetlenie klucza publicznego, oprócz tokenu. Jeśli <xref:System.Reflection.AssemblySignatureKeyAttribute> zastosowano atrybut do zestawu, token jest klucza tożsamości i jest wyświetlana nazwa algorytmu wyznaczania wartości skrótu i klucza tożsamości.<br /><br /> Zauważ, że ta opcja nie weryfikuje podpisu zestawu i nie powinna być używana do podejmowania decyzji dotyczących zaufania.  Ta opcja wyświetla jedynie surowe dane tokenu klucza publicznego.|  
|`-TS` `assembly` `infile`|Znaki testu podpisem lub częściowo podpisany `assembly` z pary kluczy w `infile`.|  
|-`TSc``assembly``container`|Znaki testu podpisem lub częściowo podpisany `assembly` z pary kluczy w kontenerze kluczy `container`.|  
|**-v** *zestawu*|Sprawdza, czy silnej nazwy w *zestawu*, gdzie *zestawu* jest nazwą pliku, który zawiera manifest zestawu.|  
|**-funkcji wirtualnej***zestawu* |Sprawdza, czy silnej nazwy w *zestawu.* W odróżnieniu od **- v** opcji **funkcji wirtualnej -** wymusza weryfikacji, nawet jeśli jest wyłączona, przy użyciu **- Vr** opcji.|  
|**-Vk***regfile.reg* *zestawu* [*userlist*] [*PlikWejściowy*]  |Tworzy plik wpisów rejestracji (reg), którego można użyć do zarejestrowania określonego zestawu, aby pomijał weryfikację. Reguły dla zestawu nazw, które są stosowane do **- Vr** opcji dotyczą **— Vk** również. Aby uzyskać informacje o *userlist* i *PlikWejściowy* opcji, zobacz **— Vr** opcji.|  
|**-Licencjonowania zbiorowego**|Wyświetla listę bieżących ustawień dla weryfikacji silnych nazw na tym komputerze.|  
|**-Vr***zestawu* [*userlist*] [*PlikWejściowy*]  |Rejestruje *zestawu* do pominięcia weryfikacji. Opcjonalnie można określić listę rozdzielonych przecinkami nazw użytkownika, do których powinno zostać zastosowane pominięcie weryfikacji. Jeśli określisz *PlikWejściowy*, weryfikacji pozostanie włączony, ale klucz publiczny w *PlikWejściowy* jest używany podczas operacji weryfikacji. Można określić *zestawu* w formularzu  *\*, strongname* do rejestrowania wszystkich zestawów o określonej nazwie silne. Aby uzyskać *strongname*, określ ciąg cyfr szesnastkowych reprezentujący tokenami formularza klucza publicznego. Zobacz **-t** i **-T** opcje, aby wyświetlić token klucza publicznego. **Uwaga:** Użyj tej opcji tylko podczas programowania. Dodanie zestawu, który będzie pomijał listę weryfikacji, tworzy lukę w zabezpieczeniach. Złośliwy zestaw mógłby użyć w pełni określonej nazwy (nazwy zestawu, wersji, kultury i tokenu klucza publicznego) zestawu dodanego do listy pomijania weryfikacji, aby ukryć swoją tożsamość. Pozwoliłoby to złośliwemu zestawowi na ominięcie weryfikacji.|  
|||  
|**-Vu***zestawu* |Wyrejestrowuje *zestawu* do pominięcia weryfikacji. Takie same zasady dla zestawu nazw, które dotyczą **- Vr** dotyczą **- Vu**.|  
|**-Vx**|Usuwa wszystkie wpisy o pomijaniu weryfikacji.|  
|**-?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
> [!NOTE]
>  We wszystkich opcjach Sn.exe rozróżniana jest wielkość liter i opcje muszą być wpisywane dokładnie tak, jak to zostało pokazane, aby zostały rozpoznane przez narzędzie.  
  
## <a name="remarks"></a>Uwagi  
 **-R** i **— Rc** opcje są przydatne w przypadku zestawów, które zostały podpisane opóźnienia. W tym scenariuszu tylko klucz publiczny został ustawiony podczas kompilacji, a podpisanie wykonywane jest później, gdy znany jest klucz prywatny.  
  
> [!NOTE]
>  Dla parametrów (na przykład —**Vr)** , które zapisują do chronionych zasobów, takich jak rejestr, uruchom SN.exe jako administrator.  
  
## <a name="examples"></a>Przykłady  
 Poniższe polecenie tworzy nowy, losowy pary kluczy i przechowuje ją w `keyPair.snk`.  
  
```  
sn -k keyPair.snk  
```  
  
 Polecenie przechowuje klucz w `keyPair.snk` w kontenerze `MyContainer` w silną nazwę dostawcy usług Kryptograficznych.  
  
```  
sn -i keyPair.snk MyContainer  
```  
  
 Polecenie wyodrębnia klucza publicznego z `keyPair.snk` i przechowuje ją w `publicKey.snk`.  
  
```  
sn -p keyPair.snk publicKey.snk  
```  
  
 Następujące polecenie wyświetla klucz publiczny i token klucza publicznego zawarte w `publicKey.snk`.  
  
```  
sn -tp publicKey.snk  
```  
  
 Polecenie sprawdza zestawu `MyAsm.dll`.  
  
```  
sn -v MyAsm.dll  
```  
  
 Następujące polecenie usuwa `MyContainer` z domyślnego dostawcy usług Kryptograficznych.  
  
```  
sn -d MyContainer  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia](../../../docs/framework/tools/index.md)  
 [Al.exe (konsolidator zestawów)](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 [Zestawy o silnych nazwach](../../../docs/framework/app-domains/strong-named-assemblies.md)  
 [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
