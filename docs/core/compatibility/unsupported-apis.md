---
title: Nieobsługiwane interfejsy API w usłudze .NET Core
titleSuffix: ''
description: Dowiedz się, które interfejsy API z platformy .NET Framework, które zawsze zgłaszają wyjątek w .NET Core.
ms.date: 12/23/2019
ms.openlocfilehash: c4b94321d30cacd90d5c2ee23c258681683a6faa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77092970"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a>Interfejsy API, które zawsze zgłaszają wyjątki w uspolonym .NET Core

Następujące interfejsy API <xref:System.PlatformNotSupportedException> zawsze będą zgłaszać na .NET Core na wszystkich lub podzbiór platform.

W tym artykule organizatorzy organizują elementy członkowskie interfejsu API, których dotyczy problem, według obszaru nazw.

> [!NOTE]
>
> - Ten artykuł jest w toku. Nie jest to pełna lista interfejsów API, które zgłaszają wyjątki w .NET Core.
> - Ten artykuł nie zawiera jawnych implementacji interfejsu dla serializacji binarnej, które wyrzucając na .NET Core. Aby uzyskać więcej informacji, zobacz [Serializacja binarna w .NET Core](../../standard/serialization/binary-serialization.md#net-core).

## <a name="system"></a>System

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | Wszystkie |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | Wszystkie |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | Wszystkie |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | Wszystkie |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | Wszystkie |

## <a name="systemcodedomcompiler"></a>System.CodeDom.Kompilator

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | Wszystkie |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | Wszystkie |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | Wszystkie |

## <a name="systemcollectionsspecialized"></a>System.collections.specialized

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | Wszystkie |

## <a name="systemconfiguration"></a>System.configuration

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType>(wszyscy członkowie) | Wszystkie |

## <a name="systemconsole"></a>System.console

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Console.BufferHeight?displayProperty=nameWithType>(tylko zestaw) | Linux i macOS |
| <xref:System.Console.BufferWidth?displayProperty=nameWithType>(tylko zestaw) | Linux i macOS |
| <xref:System.Console.CursorSize?displayProperty=nameWithType>(tylko zestaw) | Linux i macOS |
| <xref:System.Console.CursorVisible?displayProperty=nameWithType>(tylko dostać) | Linux i macOS |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Console.Title?displayProperty=nameWithType>(tylko dostać) | Linux i macOS |
| <xref:System.Console.WindowHeight?displayProperty=nameWithType>(tylko zestaw) | Linux i macOS |
| <xref:System.Console.WindowLeft?displayProperty=nameWithType>(tylko zestaw) | Linux i macOS |
| <xref:System.Console.WindowTop?displayProperty=nameWithType>(tylko zestaw) | Linux i macOS |
| <xref:System.Console.WindowWidth?displayProperty=nameWithType>(tylko zestaw) | Linux i macOS |

## <a name="systemdatacommon"></a>System.Data.Common (System.Data.Common)

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType>(rzuty) <xref:System.NotSupportedException> | Wszystkie |

## <a name="systemdiagnosticsprocess"></a>System.Diagnostics.Process (Diagnostyka.Proces)

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType>(tylko zestaw) | Linux |
| <xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType>(tylko zestaw) | Linux |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | macOS |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(tylko zestaw) | Linux i macOS |
| <xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(tylko dostać) | macOS |
| <xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType>(tylko zestaw) | Linux i macOS |

## <a name="systemio"></a>System.IO

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |

## <a name="systemiopipes"></a>System.IO.Rury

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType>(tylko zestaw) | Linux i macOS |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | Linux i macOS |

## <a name="systemmedia"></a>System.Media (System.Media)

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |

## <a name="systemnet"></a>System.Net

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |

## <a name="systemnetnetworkinformation"></a>System.Net.NetworkInformacje

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | Windows (UWP) |

## <a name="systemnetsockets"></a>System.net.sockets

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | Wszystkie |

## <a name="systemnetwebsockets"></a>System.Net.WebSockets

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | Wszystkie |

## <a name="systemreflection"></a>System.reflection

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | Wszystkie |

## <a name="systemruntimecompilerservices"></a>System.runtime.compilerservices

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | Wszystkie |

## <a name="systemruntimeinteropservices"></a>System.runtime.interopservices

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | Linux i macOS |

## <a name="systemruntimeserialization"></a>System.Runtime.Serialization

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | Wszystkie |

## <a name="systemsecurity"></a>System.Bezpieczeństwo

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | Wszystkie |

## <a name="systemsecurityclaims"></a>System.security.claims

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |

## <a name="systemsecuritycryptography"></a>System.security.cryptography

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | Wszystkie |

## <a name="systemsecuritycryptographypkcs"></a>System.Security.Cryptography.Pkcs

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | Wszystkie |

## <a name="systemsecuritycryptographyx509certificates"></a>Certyfikaty System.Security.Cryptography.X509

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType>(tylko zestaw) | Wszystkie |

## <a name="systemsecurityauthenticationextendedprotection"></a>System.Security.Authentication.ExtendedProtection

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |

## <a name="systemsecuritypolicy"></a>System.Security.Policy (System.Security.Policy)

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |

## <a name="systemserviceprocessservicecontroller"></a>Kontroler system.ServiceProcess.ServiceController

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |

## <a name="systemtextregularexpressions"></a>System.Text.RegularExpressions

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | Wszystkie |

## <a name="systemthreading"></a>System.threading

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | Wszystkie |

## <a name="systemxml"></a>System.Xml

| Członek | Platformy, które rzucają |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | Wszystkie |

## <a name="see-also"></a>Zobacz też

- [Przełomowe zmiany migracji z platformy .NET Framework do programu .NET Core](../compatibility/fx-core.md)
- [Serializacja binarna w ustom .NET Core](../../standard/serialization/binary-serialization.md#net-core)
- [Analizator przenoszenia .NET](../../standard/analyzers/portability-analyzer.md)
