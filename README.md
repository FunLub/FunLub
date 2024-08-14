Imports System
Imports System.Buffers
Imports System.Collections.Generic
Imports System.Globalization
Imports System.IO
Imports System.Linq
Imports System.Runtime.CompilerServices
Imports System.Runtime.InteropServices
Imports System.Text
Imports CompanionServer
Imports ConVar
Imports Facepunch
Imports Facepunch.Extend
Imports Facepunch.Math
Imports Facepunch.Models
Imports Facepunch.Rust
Imports JetBrains.Annotations
Imports Network
Imports Network.Visibility
Imports Newtonsoft.Json
Imports ProtoBuf
Imports ProtoBuf.Nexus
Imports Rust
Imports SilentOrbit.ProtocolBuffers
Imports UnityEngine
Imports UnityEngine.Assertions

' Token: 0x02000052 RID: 82
Public Class BasePlayer
	Inherits BaseCombatEntity
	Implements LootPanel.IHasLootPanel, IIdealSlotEntity, Global.PlayerInventory.ICanMoveFrom

	' Token: 0x060005ED RID: 1517 RVA: 0x00046520 File Offset: 0x00044720
	Public Overrides Function OnRpcMessage(player As Global.BasePlayer, rpc As UInteger, msg As Message) As Boolean
		Using TimeWarning.[New]("BasePlayer.OnRpcMessage", 0)
			If rpc = 935768323UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - ClientKeepConnectionAlive ")
				End If
				Using TimeWarning.[New]("ClientKeepConnectionAlive", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.FromOwner.Test(935768323UI, "ClientKeepConnectionAlive", Me, player) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg2 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.ClientKeepConnectionAlive(msg2)
						End Using
					Catch exception As Exception
						Debug.LogException(exception)
						player.Kick("RPC Error in ClientKeepConnectionAlive")
					End Try
				End Using
				Return True
			End If
			If rpc = 3782818894UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - ClientLoadingComplete ")
				End If
				Using TimeWarning.[New]("ClientLoadingComplete", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.FromOwner.Test(3782818894UI, "ClientLoadingComplete", Me, player) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg3 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.ClientLoadingComplete(msg3)
						End Using
					Catch exception2 As Exception
						Debug.LogException(exception2)
						player.Kick("RPC Error in ClientLoadingComplete")
					End Try
				End Using
				Return True
			End If
			If rpc = 1497207530UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - IssuePetCommand ")
				End If
				Using TimeWarning.[New]("IssuePetCommand", 0)
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg4 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.IssuePetCommand(msg4)
						End Using
					Catch exception3 As Exception
						Debug.LogException(exception3)
						player.Kick("RPC Error in IssuePetCommand")
					End Try
				End Using
				Return True
			End If
			If rpc = 2041023702UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - IssuePetCommandRaycast ")
				End If
				Using TimeWarning.[New]("IssuePetCommandRaycast", 0)
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg5 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.IssuePetCommandRaycast(msg5)
						End Using
					Catch exception4 As Exception
						Debug.LogException(exception4)
						player.Kick("RPC Error in IssuePetCommandRaycast")
					End Try
				End Using
				Return True
			End If
			If rpc = 495414158UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - NotifyDebugCameraEnded ")
				End If
				Using TimeWarning.[New]("NotifyDebugCameraEnded", 0)
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg6 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.NotifyDebugCameraEnded(msg6)
						End Using
					Catch exception5 As Exception
						Debug.LogException(exception5)
						player.Kick("RPC Error in NotifyDebugCameraEnded")
					End Try
				End Using
				Return True
			End If
			If rpc = 3441821928UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - OnFeedbackReport ")
				End If
				Using TimeWarning.[New]("OnFeedbackReport", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.CallsPerSecond.Test(3441821928UI, "OnFeedbackReport", Me, player, 1UL) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg7 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.OnFeedbackReport(msg7)
						End Using
					Catch exception6 As Exception
						Debug.LogException(exception6)
						player.Kick("RPC Error in OnFeedbackReport")
					End Try
				End Using
				Return True
			End If
			If rpc = 1998170713UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - OnPlayerLanded ")
				End If
				Using TimeWarning.[New]("OnPlayerLanded", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.FromOwner.Test(1998170713UI, "OnPlayerLanded", Me, player) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg8 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.OnPlayerLanded(msg8)
						End Using
					Catch exception7 As Exception
						Debug.LogException(exception7)
						player.Kick("RPC Error in OnPlayerLanded")
					End Try
				End Using
				Return True
			End If
			If rpc = 2147041557UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - OnPlayerReported ")
				End If
				Using TimeWarning.[New]("OnPlayerReported", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.CallsPerSecond.Test(2147041557UI, "OnPlayerReported", Me, player, 1UL) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg9 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.OnPlayerReported(msg9)
						End Using
					Catch exception8 As Exception
						Debug.LogException(exception8)
						player.Kick("RPC Error in OnPlayerReported")
					End Try
				End Using
				Return True
			End If
			If rpc = 363681694UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - OnProjectileAttack ")
				End If
				Using TimeWarning.[New]("OnProjectileAttack", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.FromOwner.Test(363681694UI, "OnProjectileAttack", Me, player) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg10 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.OnProjectileAttack(msg10)
						End Using
					Catch exception9 As Exception
						Debug.LogException(exception9)
						player.Kick("RPC Error in OnProjectileAttack")
					End Try
				End Using
				Return True
			End If
			If rpc = 1500391289UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - OnProjectileRicochet ")
				End If
				Using TimeWarning.[New]("OnProjectileRicochet", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.FromOwner.Test(1500391289UI, "OnProjectileRicochet", Me, player) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg11 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.OnProjectileRicochet(msg11)
						End Using
					Catch exception10 As Exception
						Debug.LogException(exception10)
						player.Kick("RPC Error in OnProjectileRicochet")
					End Try
				End Using
				Return True
			End If
			If rpc = 2324190493UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - OnProjectileUpdate ")
				End If
				Using TimeWarning.[New]("OnProjectileUpdate", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.FromOwner.Test(2324190493UI, "OnProjectileUpdate", Me, player) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg12 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.OnProjectileUpdate(msg12)
						End Using
					Catch exception11 As Exception
						Debug.LogException(exception11)
						player.Kick("RPC Error in OnProjectileUpdate")
					End Try
				End Using
				Return True
			End If
			If rpc = 3167788018UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - PerformanceReport ")
				End If
				Using TimeWarning.[New]("PerformanceReport", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.CallsPerSecond.Test(3167788018UI, "PerformanceReport", Me, player, 1UL) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg13 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.PerformanceReport(msg13)
						End Using
					Catch exception12 As Exception
						Debug.LogException(exception12)
						player.Kick("RPC Error in PerformanceReport")
					End Try
				End Using
				Return True
			End If
			If rpc = 420048204UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - PerformanceReport_Frametime ")
				End If
				Using TimeWarning.[New]("PerformanceReport_Frametime", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.CallsPerSecond.Test(420048204UI, "PerformanceReport_Frametime", Me, player, 1UL) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg14 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.PerformanceReport_Frametime(msg14)
						End Using
					Catch exception13 As Exception
						Debug.LogException(exception13)
						player.Kick("RPC Error in PerformanceReport_Frametime")
					End Try
				End Using
				Return True
			End If
			If rpc = 4081064578UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - PlayerRequestedTutorialStart ")
				End If
				Using TimeWarning.[New]("PlayerRequestedTutorialStart", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.CallsPerSecond.Test(4081064578UI, "PlayerRequestedTutorialStart", Me, player, 1UL) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg15 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.PlayerRequestedTutorialStart(msg15)
						End Using
					Catch exception14 As Exception
						Debug.LogException(exception14)
						player.Kick("RPC Error in PlayerRequestedTutorialStart")
					End Try
				End Using
				Return True
			End If
			If rpc = 1024003327UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - RequestParachuteDeploy ")
				End If
				Using TimeWarning.[New]("RequestParachuteDeploy", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.CallsPerSecond.Test(1024003327UI, "RequestParachuteDeploy", Me, player, 5UL) Then
							Return True
						End If
						If Not Global.BaseEntity.RPC_Server.FromOwner.Test(1024003327UI, "RequestParachuteDeploy", Me, player) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg16 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.RequestParachuteDeploy(msg16)
						End Using
					Catch exception15 As Exception
						Debug.LogException(exception15)
						player.Kick("RPC Error in RequestParachuteDeploy")
					End Try
				End Using
				Return True
			End If
			If rpc = 52352806UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - RequestRespawnInformation ")
				End If
				Using TimeWarning.[New]("RequestRespawnInformation", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.CallsPerSecond.Test(52352806UI, "RequestRespawnInformation", Me, player, 1UL) Then
							Return True
						End If
						If Not Global.BaseEntity.RPC_Server.FromOwner.Test(52352806UI, "RequestRespawnInformation", Me, player) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg17 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.RequestRespawnInformation(msg17)
						End Using
					Catch exception16 As Exception
						Debug.LogException(exception16)
						player.Kick("RPC Error in RequestRespawnInformation")
					End Try
				End Using
				Return True
			End If
			If rpc = 1774681338UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - RequestServerEmoji ")
				End If
				Using TimeWarning.[New]("RequestServerEmoji", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.CallsPerSecond.Test(1774681338UI, "RequestServerEmoji", Me, player, 1UL) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Me.RequestServerEmoji()
						End Using
					Catch exception17 As Exception
						Debug.LogException(exception17)
						player.Kick("RPC Error in RequestServerEmoji")
					End Try
				End Using
				Return True
			End If
			If rpc = 970468557UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - RPC_Assist ")
				End If
				Using TimeWarning.[New]("RPC_Assist", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.IsVisible.Test(970468557UI, "RPC_Assist", Me, player, 3F) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg18 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.RPC_Assist(msg18)
						End Using
					Catch exception18 As Exception
						Debug.LogException(exception18)
						player.Kick("RPC Error in RPC_Assist")
					End Try
				End Using
				Return True
			End If
			If rpc = 3263238541UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - RPC_KeepAlive ")
				End If
				Using TimeWarning.[New]("RPC_KeepAlive", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.IsVisible.Test(3263238541UI, "RPC_KeepAlive", Me, player, 3F) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg19 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.RPC_KeepAlive(msg19)
						End Using
					Catch exception19 As Exception
						Debug.LogException(exception19)
						player.Kick("RPC Error in RPC_KeepAlive")
					End Try
				End Using
				Return True
			End If
			If rpc = 3692395068UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - RPC_LootPlayer ")
				End If
				Using TimeWarning.[New]("RPC_LootPlayer", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.IsVisible.Test(3692395068UI, "RPC_LootPlayer", Me, player, 3F) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg20 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.RPC_LootPlayer(msg20)
						End Using
					Catch exception20 As Exception
						Debug.LogException(exception20)
						player.Kick("RPC Error in RPC_LootPlayer")
					End Try
				End Using
				Return True
			End If
			If rpc = 439739525UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - RPC_ReqDoPush ")
				End If
				Using TimeWarning.[New]("RPC_ReqDoPush", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.CallsPerSecond.Test(439739525UI, "RPC_ReqDoPush", Me, player, 5UL) Then
							Return True
						End If
						If Not Global.BaseEntity.RPC_Server.IsVisible.Test(439739525UI, "RPC_ReqDoPush", Me, player, 3F) Then
							Return True
						End If
						If Not Global.BaseEntity.RPC_Server.MaxDistance.Test(439739525UI, "RPC_ReqDoPush", Me, player, 3F, False) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim rpc2 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.RPC_ReqDoPush(rpc2)
						End Using
					Catch exception21 As Exception
						Debug.LogException(exception21)
						player.Kick("RPC Error in RPC_ReqDoPush")
					End Try
				End Using
				Return True
			End If
			If rpc = 3974264977UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - RPC_ReqEquipHood ")
				End If
				Using TimeWarning.[New]("RPC_ReqEquipHood", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.CallsPerSecond.Test(3974264977UI, "RPC_ReqEquipHood", Me, player, 5UL) Then
							Return True
						End If
						If Not Global.BaseEntity.RPC_Server.IsVisible.Test(3974264977UI, "RPC_ReqEquipHood", Me, player, 3F) Then
							Return True
						End If
						If Not Global.BaseEntity.RPC_Server.MaxDistance.Test(3974264977UI, "RPC_ReqEquipHood", Me, player, 3F, False) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim rpc3 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.RPC_ReqEquipHood(rpc3)
						End Using
					Catch exception22 As Exception
						Debug.LogException(exception22)
						player.Kick("RPC Error in RPC_ReqEquipHood")
					End Try
				End Using
				Return True
			End If
			If rpc = 4144905368UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - RPC_ReqForceMountNearest ")
				End If
				Using TimeWarning.[New]("RPC_ReqForceMountNearest", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.CallsPerSecond.Test(4144905368UI, "RPC_ReqForceMountNearest", Me, player, 5UL) Then
							Return True
						End If
						If Not Global.BaseEntity.RPC_Server.IsVisible.Test(4144905368UI, "RPC_ReqForceMountNearest", Me, player, 3F) Then
							Return True
						End If
						If Not Global.BaseEntity.RPC_Server.MaxDistance.Test(4144905368UI, "RPC_ReqForceMountNearest", Me, player, 3F, False) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim rpc4 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.RPC_ReqForceMountNearest(rpc4)
						End Using
					Catch exception23 As Exception
						Debug.LogException(exception23)
						player.Kick("RPC Error in RPC_ReqForceMountNearest")
					End Try
				End Using
				Return True
			End If
			If rpc = 3816898909UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - RPC_ReqForceSwapSeat ")
				End If
				Using TimeWarning.[New]("RPC_ReqForceSwapSeat", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.CallsPerSecond.Test(3816898909UI, "RPC_ReqForceSwapSeat", Me, player, 5UL) Then
							Return True
						End If
						If Not Global.BaseEntity.RPC_Server.IsVisible.Test(3816898909UI, "RPC_ReqForceSwapSeat", Me, player, 3F) Then
							Return True
						End If
						If Not Global.BaseEntity.RPC_Server.MaxDistance.Test(3816898909UI, "RPC_ReqForceSwapSeat", Me, player, 3F, False) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim rpc5 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.RPC_ReqForceSwapSeat(rpc5)
						End Using
					Catch exception24 As Exception
						Debug.LogException(exception24)
						player.Kick("RPC Error in RPC_ReqForceSwapSeat")
					End Try
				End Using
				Return True
			End If
			If rpc = 626234931UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - RPC_ReqRemoveCuffs ")
				End If
				Using TimeWarning.[New]("RPC_ReqRemoveCuffs", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.CallsPerSecond.Test(626234931UI, "RPC_ReqRemoveCuffs", Me, player, 5UL) Then
							Return True
						End If
						If Not Global.BaseEntity.RPC_Server.IsVisible.Test(626234931UI, "RPC_ReqRemoveCuffs", Me, player, 3F) Then
							Return True
						End If
						If Not Global.BaseEntity.RPC_Server.MaxDistance.Test(626234931UI, "RPC_ReqRemoveCuffs", Me, player, 3F, False) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim rpc6 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.RPC_ReqRemoveCuffs(rpc6)
						End Using
					Catch exception25 As Exception
						Debug.LogException(exception25)
						player.Kick("RPC Error in RPC_ReqRemoveCuffs")
					End Try
				End Using
				Return True
			End If
			If rpc = 2289764809UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - RPC_ReqRemoveHood ")
				End If
				Using TimeWarning.[New]("RPC_ReqRemoveHood", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.CallsPerSecond.Test(2289764809UI, "RPC_ReqRemoveHood", Me, player, 5UL) Then
							Return True
						End If
						If Not Global.BaseEntity.RPC_Server.IsVisible.Test(2289764809UI, "RPC_ReqRemoveHood", Me, player, 3F) Then
							Return True
						End If
						If Not Global.BaseEntity.RPC_Server.MaxDistance.Test(2289764809UI, "RPC_ReqRemoveHood", Me, player, 3F, False) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim rpc7 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.RPC_ReqRemoveHood(rpc7)
						End Using
					Catch exception26 As Exception
						Debug.LogException(exception26)
						player.Kick("RPC Error in RPC_ReqRemoveHood")
					End Try
				End Using
				Return True
			End If
			If rpc = 1539133504UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - RPC_StartClimb ")
				End If
				Using TimeWarning.[New]("RPC_StartClimb", 0)
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg21 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.RPC_StartClimb(msg21)
						End Using
					Catch exception27 As Exception
						Debug.LogException(exception27)
						player.Kick("RPC Error in RPC_StartClimb")
					End Try
				End Using
				Return True
			End If
			If rpc = 3047177092UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - Server_AddMarker ")
				End If
				Using TimeWarning.[New]("Server_AddMarker", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.CallsPerSecond.Test(3047177092UI, "Server_AddMarker", Me, player, 8UL) Then
							Return True
						End If
						If Not Global.BaseEntity.RPC_Server.FromOwner.Test(3047177092UI, "Server_AddMarker", Me, player) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg22 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.Server_AddMarker(msg22)
						End Using
					Catch exception28 As Exception
						Debug.LogException(exception28)
						player.Kick("RPC Error in Server_AddMarker")
					End Try
				End Using
				Return True
			End If
			If rpc = 3618659425UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - Server_AddPing ")
				End If
				Using TimeWarning.[New]("Server_AddPing", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.CallsPerSecond.Test(3618659425UI, "Server_AddPing", Me, player, 3UL) Then
							Return True
						End If
						If Not Global.BaseEntity.RPC_Server.FromOwner.Test(3618659425UI, "Server_AddPing", Me, player) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg23 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.Server_AddPing(msg23)
						End Using
					Catch exception29 As Exception
						Debug.LogException(exception29)
						player.Kick("RPC Error in Server_AddPing")
					End Try
				End Using
				Return True
			End If
			If rpc = 1005040107UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - Server_CancelGesture ")
				End If
				Using TimeWarning.[New]("Server_CancelGesture", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.CallsPerSecond.Test(1005040107UI, "Server_CancelGesture", Me, player, 10UL) Then
							Return True
						End If
						If Not Global.BaseEntity.RPC_Server.FromOwner.Test(1005040107UI, "Server_CancelGesture", Me, player) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Me.Server_CancelGesture()
						End Using
					Catch exception30 As Exception
						Debug.LogException(exception30)
						player.Kick("RPC Error in Server_CancelGesture")
					End Try
				End Using
				Return True
			End If
			If rpc = 706157120UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - Server_ClearMapMarkers ")
				End If
				Using TimeWarning.[New]("Server_ClearMapMarkers", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.CallsPerSecond.Test(706157120UI, "Server_ClearMapMarkers", Me, player, 1UL) Then
							Return True
						End If
						If Not Global.BaseEntity.RPC_Server.FromOwner.Test(706157120UI, "Server_ClearMapMarkers", Me, player) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg24 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.Server_ClearMapMarkers(msg24)
						End Using
					Catch exception31 As Exception
						Debug.LogException(exception31)
						player.Kick("RPC Error in Server_ClearMapMarkers")
					End Try
				End Using
				Return True
			End If
			If rpc = 1032755717UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - Server_RemovePing ")
				End If
				Using TimeWarning.[New]("Server_RemovePing", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.CallsPerSecond.Test(1032755717UI, "Server_RemovePing", Me, player, 3UL) Then
							Return True
						End If
						If Not Global.BaseEntity.RPC_Server.FromOwner.Test(1032755717UI, "Server_RemovePing", Me, player) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg25 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.Server_RemovePing(msg25)
						End Using
					Catch exception32 As Exception
						Debug.LogException(exception32)
						player.Kick("RPC Error in Server_RemovePing")
					End Try
				End Using
				Return True
			End If
			If rpc = 31713840UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - Server_RemovePointOfInterest ")
				End If
				Using TimeWarning.[New]("Server_RemovePointOfInterest", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.CallsPerSecond.Test(31713840UI, "Server_RemovePointOfInterest", Me, player, 10UL) Then
							Return True
						End If
						If Not Global.BaseEntity.RPC_Server.FromOwner.Test(31713840UI, "Server_RemovePointOfInterest", Me, player) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg26 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.Server_RemovePointOfInterest(msg26)
						End Using
					Catch exception33 As Exception
						Debug.LogException(exception33)
						player.Kick("RPC Error in Server_RemovePointOfInterest")
					End Try
				End Using
				Return True
			End If
			If rpc = 2567683804UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - Server_RequestMarkers ")
				End If
				Using TimeWarning.[New]("Server_RequestMarkers", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.CallsPerSecond.Test(2567683804UI, "Server_RequestMarkers", Me, player, 1UL) Then
							Return True
						End If
						If Not Global.BaseEntity.RPC_Server.FromOwner.Test(2567683804UI, "Server_RequestMarkers", Me, player) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg27 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.Server_RequestMarkers(msg27)
						End Using
					Catch exception34 As Exception
						Debug.LogException(exception34)
						player.Kick("RPC Error in Server_RequestMarkers")
					End Try
				End Using
				Return True
			End If
			If rpc = 1572722245UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - Server_StartGesture ")
				End If
				Using TimeWarning.[New]("Server_StartGesture", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.CallsPerSecond.Test(1572722245UI, "Server_StartGesture", Me, player, 1UL) Then
							Return True
						End If
						If Not Global.BaseEntity.RPC_Server.FromOwner.Test(1572722245UI, "Server_StartGesture", Me, player) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg28 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.Server_StartGesture(msg28)
						End Using
					Catch exception35 As Exception
						Debug.LogException(exception35)
						player.Kick("RPC Error in Server_StartGesture")
					End Try
				End Using
				Return True
			End If
			If rpc = 1180369886UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - Server_UpdateMarker ")
				End If
				Using TimeWarning.[New]("Server_UpdateMarker", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.CallsPerSecond.Test(1180369886UI, "Server_UpdateMarker", Me, player, 1UL) Then
							Return True
						End If
						If Not Global.BaseEntity.RPC_Server.FromOwner.Test(1180369886UI, "Server_UpdateMarker", Me, player) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg29 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.Server_UpdateMarker(msg29)
						End Using
					Catch exception36 As Exception
						Debug.LogException(exception36)
						player.Kick("RPC Error in Server_UpdateMarker")
					End Try
				End Using
				Return True
			End If
			If rpc = 2192544725UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - ServerRequestEmojiData ")
				End If
				Using TimeWarning.[New]("ServerRequestEmojiData", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.CallsPerSecond.Test(2192544725UI, "ServerRequestEmojiData", Me, player, 3UL) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg30 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.ServerRequestEmojiData(msg30)
						End Using
					Catch exception37 As Exception
						Debug.LogException(exception37)
						player.Kick("RPC Error in ServerRequestEmojiData")
					End Try
				End Using
				Return True
			End If
			If rpc = 3635568749UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - ServerRPC_UnderwearChange ")
				End If
				Using TimeWarning.[New]("ServerRPC_UnderwearChange", 0)
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg31 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.ServerRPC_UnderwearChange(msg31)
						End Using
					Catch exception38 As Exception
						Debug.LogException(exception38)
						player.Kick("RPC Error in ServerRPC_UnderwearChange")
					End Try
				End Using
				Return True
			End If
			If rpc = 3222472445UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - StartTutorial ")
				End If
				Using TimeWarning.[New]("StartTutorial", 0)
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg32 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.StartTutorial(msg32)
						End Using
					Catch exception39 As Exception
						Debug.LogException(exception39)
						player.Kick("RPC Error in StartTutorial")
					End Try
				End Using
				Return True
			End If
			If rpc = 970114602UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - SV_Drink ")
				End If
				Using TimeWarning.[New]("SV_Drink", 0)
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg33 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.SV_Drink(msg33)
						End Using
					Catch exception40 As Exception
						Debug.LogException(exception40)
						player.Kick("RPC Error in SV_Drink")
					End Try
				End Using
				Return True
			End If
			If rpc = 1361044246UI AndAlso player IsNot Nothing Then
				Assert.IsTrue(player.isServer, "SV_RPC Message is using a clientside player!")
				If ConVar.[Global].developer > 2 Then
					Debug.Log("SV_RPCMessage: " + If((player IsNot Nothing), player.ToString(), Nothing) + " - UpdateSpectatePositionFromDebugCamera ")
				End If
				Using TimeWarning.[New]("UpdateSpectatePositionFromDebugCamera", 0)
					Using TimeWarning.[New]("Conditions", 0)
						If Not Global.BaseEntity.RPC_Server.CallsPerSecond.Test(1361044246UI, "UpdateSpectatePositionFromDebugCamera", Me, player, 10UL) Then
							Return True
						End If
						If Not Global.BaseEntity.RPC_Server.FromOwner.Test(1361044246UI, "UpdateSpectatePositionFromDebugCamera", Me, player) Then
							Return True
						End If
					End Using
					Try
						Using TimeWarning.[New]("Call", 0)
							Dim msg34 As Global.BaseEntity.RPCMessage = New Global.BaseEntity.RPCMessage() With { .connection = msg.connection, .player = player, .read = msg.read }
							Me.UpdateSpectatePositionFromDebugCamera(msg34)
						End Using
					Catch exception41 As Exception
						Debug.LogException(exception41)
						player.Kick("RPC Error in UpdateSpectatePositionFromDebugCamera")
					End Try
				End Using
				Return True
			End If
		End Using
		Return MyBase.OnRpcMessage(player, rpc, msg)
	End Function

	' Token: 0x060005EE RID: 1518 RVA: 0x00049EA4 File Offset: 0x000480A4
	Public Function TriggeredAntiHack(Optional seconds As Single = 1F, Optional score As Single = Single.PositiveInfinity) As Boolean
		Return UnityEngine.Time.realtimeSinceStartup - Me.lastViolationTime < seconds OrElse Me.violationLevel > score
	End Function

	' Token: 0x060005EF RID: 1519 RVA: 0x00049EC0 File Offset: 0x000480C0
	Public Function UsedAdminCheat(Optional seconds As Single = 2F) As Boolean
		Return UnityEngine.Time.realtimeSinceStartup - Me.lastAdminCheatTime < seconds
	End Function

	' Token: 0x060005F0 RID: 1520 RVA: 0x00049ED1 File Offset: 0x000480D1
	Public Sub PauseVehicleNoClipDetection(Optional seconds As Single = 1F)
		Me.vehiclePauseTime = Mathf.Max(Me.vehiclePauseTime, seconds)
	End Sub

	' Token: 0x060005F1 RID: 1521 RVA: 0x00049EE5 File Offset: 0x000480E5
	Public Sub PauseFlyHackDetection(Optional seconds As Single = 1F)
		Me.flyhackPauseTime = Mathf.Max(Me.flyhackPauseTime, seconds)
	End Sub

	' Token: 0x060005F2 RID: 1522 RVA: 0x00049EF9 File Offset: 0x000480F9
	Public Sub PauseSpeedHackDetection(Optional seconds As Single = 1F)
		Me.speedhackPauseTime = Mathf.Max(Me.speedhackPauseTime, seconds)
	End Sub

	' Token: 0x060005F3 RID: 1523 RVA: 0x00049F0D File Offset: 0x0004810D
	Public Function GetAntiHackKicks() As Integer
		Return Global.AntiHack.GetKickRecord(Me)
	End Function

	' Token: 0x060005F4 RID: 1524 RVA: 0x00049F18 File Offset: 0x00048118
	Public Sub ResetAntiHack()
		Me.violationLevel = 0F
		Me.lastViolationTime = 0F
		Me.lastAdminCheatTime = 0F
		Me.speedhackPauseTime = 0F
		Me.speedhackDistance = 0F
		Me.flyhackPauseTime = 0F
		Me.flyhackDistanceVertical = 0F
		Me.flyhackDistanceHorizontal = 0F
		Me.rpcHistory.Clear()
	End Sub

	' Token: 0x060005F5 RID: 1525 RVA: 0x00049F88 File Offset: 0x00048188
	Public Function CanModifyClan() As Boolean
		If Not Clan.editsRequireClanTable Then
			Return True
		End If
		If Not MyBase.isServer Then
			Return False
		End If
		If Me.triggers Is Nothing OrElse Global.ClanManager.ServerInstance Is Nothing Then
			Return False
		End If
		Using enumerator As List(Of TriggerBase).Enumerator = Me.triggers.GetEnumerator()
			While enumerator.MoveNext()
				If TypeOf enumerator.Current Is TriggerClanModify Then
					Return True
				End If
			End While
		End Using
		Return False
	End Function

	' Token: 0x060005F6 RID: 1526 RVA: 0x0004A00C File Offset: 0x0004820C
	Public Sub LoadClanInfo()
		Dim CS$<>8__locals1 As Global.BasePlayer.<>c__DisplayClass33_0 = New Global.BasePlayer.<>c__DisplayClass33_0()
		CS$<>8__locals1.<>4__this = Me
		CS$<>8__locals1.clanManager = Global.ClanManager.ServerInstance
		If CS$<>8__locals1.clanManager Is Nothing Then
			Return
		End If
		CS$<>8__locals1.<LoadClanInfo>g__LoadClanInfoImpl|0()
	End Sub

	' Token: 0x060005F7 RID: 1527 RVA: 0x0004A048 File Offset: 0x00048248
	Public Sub UpdateClanLastSeen()
		Dim CS$<>8__locals1 As Global.BasePlayer.<>c__DisplayClass34_0 = New Global.BasePlayer.<>c__DisplayClass34_0()
		CS$<>8__locals1.<>4__this = Me
		CS$<>8__locals1.clanManager = Global.ClanManager.ServerInstance
		If CS$<>8__locals1.clanManager Is Nothing OrElse Me.clanId = 0L Then
			Return
		End If
		CS$<>8__locals1.<UpdateClanLastSeen>g__UpdateClanLastSeenImpl|0()
	End Sub

	' Token: 0x060005F8 RID: 1528 RVA: 0x0004A08C File Offset: 0x0004828C
	Public Sub AddClanScore(type As ClanScoreEventType, Optional multiplier As Integer = 1, Optional otherPlayer As Global.BasePlayer = Nothing, Optional otherClan As IClan = Nothing, Optional arg1 As String = Nothing, Optional arg2 As String = Nothing)
		Dim serverInstance As Global.ClanManager = Global.ClanManager.ServerInstance
		If serverInstance Is Nothing OrElse Me.serverClan Is Nothing OrElse Me.IsBot OrElse Me.IsNpc OrElse multiplier = 0 Then
			Return
		End If
		Dim scoreForEvent As Integer = Clan.GetScoreForEvent(type)
		If scoreForEvent = 0 Then
			Return
		End If
		Dim flag As Boolean = otherPlayer IsNot Nothing AndAlso Not otherPlayer.IsBot AndAlso Not otherPlayer.IsNpc
		serverInstance.AddScore(Me.serverClan, New ClanScoreEvent() With { .Type = type, .SteamId = New ULong?(Me.userID), .Score = scoreForEvent, .Multiplier = multiplier, .OtherSteamId = If(flag, New ULong?(otherPlayer.userID), Nothing), .OtherClanId = If((otherClan IsNot Nothing AndAlso otherClan IsNot Me.serverClan), New Long?(otherClan.ClanId), If((flag AndAlso otherPlayer.clanId <> 0L), New Long?(otherPlayer.clanId), Nothing)), .Arg1 = arg1, .Arg2 = arg2 })
	End Sub

	' Token: 0x060005F9 RID: 1529 RVA: 0x0004A1B0 File Offset: 0x000483B0
	Private Sub HandleClanPlayerKilled(killedByPlayer As Global.BasePlayer)
		If Me.serverClan IsNot Nothing AndAlso killedByPlayer.serverClan IsNot Nothing AndAlso Me.serverClan IsNot killedByPlayer.serverClan Then
			Me.AddClanScore(ClanScoreEventType.ClanPlayerDied, 1, killedByPlayer, Nothing, Nothing, Nothing)
			killedByPlayer.AddClanScore(ClanScoreEventType.ClanPlayerKilled, 1, Me, Nothing, Nothing, Nothing)
		End If
		If Not Me.HasPlayerFlag(Global.BasePlayer.PlayerFlags.DisplaySash) AndAlso killedByPlayer.serverClan IsNot Nothing Then
			killedByPlayer.AddClanScore(ClanScoreEventType.UnarmedPlayerKilled, 1, Me, Nothing, Nothing, Nothing)
		End If
	End Sub

	' Token: 0x060005FA RID: 1530 RVA: 0x0004A214 File Offset: 0x00048414
	Public Overrides Function CanBeLooted(player As Global.BasePlayer) As Boolean
		Return Not(player Is Me) AndAlso ((Me.IsWounded() OrElse Me.IsSleeping() OrElse Me.CurrentGestureIsSurrendering OrElse Me.IsRestrainedOrSurrendering) AndAlso Not Me.IsLoadingAfterTransfer()) AndAlso Not MyBase.IsTransferring()
	End Function

	' Token: 0x170000A8 RID: 168
	' (get) Token: 0x060005FB RID: 1531 RVA: 0x0004A254 File Offset: 0x00048454
	Public ReadOnly Property LootPanelTitle As Translate.Phrase Implements LootPanel.IHasLootPanel.LootPanelTitle
		Get
			Return Me.displayName
		End Get
	End Property

	' Token: 0x060005FC RID: 1532 RVA: 0x0004A264 File Offset: 0x00048464
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.IsVisible(3F)>
	Public Sub RPC_LootPlayer(msg As Global.BaseEntity.RPCMessage)
		Dim player As Global.BasePlayer = msg.player
		If Not player OrElse Not player.CanInteract() Then
			Return
		End If
		If Not Me.CanBeLooted(player) Then
			Return
		End If
		If player.inventory.loot.StartLootingEntity(Me, True) Then
			player.inventory.loot.AddContainer(Me.inventory.containerMain)
			player.inventory.loot.AddContainer(Me.inventory.containerWear)
			player.inventory.loot.AddContainer(Me.inventory.containerBelt)
			player.inventory.loot.SendImmediate()
			player.ClientRPC(Of String)(RpcTarget.Player("RPC_OpenLootPanel", player), "player_corpse")
		End If
	End Sub

	' Token: 0x060005FD RID: 1533 RVA: 0x0004A320 File Offset: 0x00048520
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.IsVisible(3F)>
	Public Sub RPC_Assist(msg As Global.BaseEntity.RPCMessage)
		If Not msg.player.CanInteract() Then
			Return
		End If
		If msg.player Is Me Then
			Return
		End If
		If Not Me.IsWounded() Then
			Return
		End If
		Me.StopWounded(msg.player)
		msg.player.stats.Add("wounded_assisted", 1, CType(5, Global.Stats))
		Me.stats.Add("wounded_healed", 1, Global.Stats.Steam)
	End Sub

	' Token: 0x060005FE RID: 1534 RVA: 0x0004A388 File Offset: 0x00048588
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.IsVisible(3F)>
	Public Sub RPC_KeepAlive(msg As Global.BaseEntity.RPCMessage)
		If Not msg.player.CanInteract() Then
			Return
		End If
		If msg.player Is Me Then
			Return
		End If
		If Not Me.IsWounded() Then
			Return
		End If
		Me.ProlongWounding(10F)
	End Sub

	' Token: 0x060005FF RID: 1535 RVA: 0x0004A3BC File Offset: 0x000485BC
	<Global.BaseEntity.RPC_Server()>
	Private Sub SV_Drink(msg As Global.BaseEntity.RPCMessage)
		Dim player As Global.BasePlayer = msg.player
		Dim vector As Vector3 = msg.read.Vector3()
		If vector.IsNaNOrInfinity() Then
			Return
		End If
		If Not player Then
			Return
		End If
		If Not player.metabolism.CanConsume() Then
			Return
		End If
		If Vector3.Distance(player.transform.position, vector) > 5F Then
			Return
		End If
		If Not WaterLevel.Test(vector, True, True, Me) Then
			Return
		End If
		If Me.isMounted AndAlso Not Me.GetMounted().canDrinkWhileMounted Then
			Return
		End If
		Dim atPoint As ItemDefinition = WaterResource.GetAtPoint(vector)
		If atPoint Is Nothing Then
			Return
		End If
		Dim component As ItemModConsumable = atPoint.GetComponent(Of ItemModConsumable)()
		Dim item As Global.Item = ItemManager.Create(atPoint, component.amountToConsume, 0UL)
		Dim component2 As ItemModConsume = item.info.GetComponent(Of ItemModConsume)()
		If component2.CanDoAction(item, player) Then
			component2.DoAction(item, player)
		End If
		If item IsNot Nothing Then
			item.Remove(0F)
		End If
		player.metabolism.MarkConsumption()
	End Sub

	' Token: 0x06000600 RID: 1536 RVA: 0x0004A4A0 File Offset: 0x000486A0
	<Global.BaseEntity.RPC_Server()>
	Public Sub RPC_StartClimb(msg As Global.BaseEntity.RPCMessage)
		Dim player As Global.BasePlayer = msg.player
		Dim flag As Boolean = msg.read.Bit()
		Dim vector As Vector3 = msg.read.Vector3()
		Dim networkableId As NetworkableId = msg.read.EntityID()
		Dim baseNetworkable As Global.BaseNetworkable = Global.BaseNetworkable.serverEntities.Find(networkableId)
		Dim vector2 As Vector3 = If(flag, baseNetworkable.transform.TransformPoint(vector), vector)
		If Not player.isMounted Then
			Return
		End If
		If player.Distance(vector2) > 5F Then
			Return
		End If
		If Not GamePhysics.LineOfSight(player.eyes.position, vector2, 1218519041, Nothing) Then
			Return
		End If
		If Not GamePhysics.LineOfSight(vector2, vector2 + player.eyes.offset, 1218519041, Nothing) Then
			Return
		End If
		Dim [end] As Vector3 = vector2 - (vector2 - player.eyes.position).normalized * 0.25F
		If GamePhysics.CheckCapsule(player.eyes.position, [end], 0.25F, 1218519041, QueryTriggerInteraction.UseGlobal) Then
			Return
		End If
		Dim collider As Collider
		If Global.AntiHack.TestNoClipping(vector2 + player.NoClipOffset(), vector2 + player.NoClipOffset(), player.NoClipRadius(ConVar.AntiHack.noclip_margin), ConVar.AntiHack.noclip_backtracking, True, collider, False, Nothing) Then
			Return
		End If
		player.EnsureDismounted()
		player.transform.position = vector2
		Dim component As Collider = player.GetComponent(Of Collider)()
		component.enabled = False
		component.enabled = True
		player.ForceUpdateTriggers(True, True, True)
		If flag Then
			player.ClientRPC(Of Vector3, NetworkableId)(RpcTarget.Player("ForcePositionToParentOffset", player), vector, networkableId)
			Return
		End If
		player.ClientRPC(Of Vector3)(RpcTarget.Player("ForcePositionTo", player), vector2)
	End Sub

	' Token: 0x06000601 RID: 1537 RVA: 0x0004A62E File Offset: 0x0004882E
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.CallsPerSecond(1UL)>
	Private Sub RequestServerEmoji()
		RustEmojiLibrary.FindAllServerEmoji()
		If RustEmojiLibrary.allServerEmoji.Count > 0 Then
			MyBase.ClientRPCPlayerList(Of String)(Nothing, Me, "ClientReceiveEmojiList", RustEmojiLibrary.cachedServerList)
		End If
	End Sub

	' Token: 0x06000602 RID: 1538 RVA: 0x0004A654 File Offset: 0x00048854
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.CallsPerSecond(3UL)>
	Private Sub ServerRequestEmojiData(msg As Global.BaseEntity.RPCMessage)
		Dim text As String = msg.read.[String](256, False)
		Dim serverEmojiConfig As RustEmojiLibrary.ServerEmojiConfig
		If RustEmojiLibrary.allServerEmoji.TryGetValue(text, serverEmojiConfig) Then
			Dim array As Byte() = FileStorage.server.[Get](serverEmojiConfig.CRC, serverEmojiConfig.FileType, RustEmojiLibrary.EmojiStorageNetworkId, 0UI)
			MyBase.ClientRPC(Of UInteger, Byte(), String, UInteger, Integer)(RpcTarget.Player("ClientReceiveEmojiData", msg.player), CUInt(array.Length), array, text, serverEmojiConfig.CRC, CInt(serverEmojiConfig.FileType))
		End If
	End Sub

	' Token: 0x06000603 RID: 1539 RVA: 0x0004A6C6 File Offset: 0x000488C6
	Public Function GetQueuedUpdateCount(queue As Global.BasePlayer.NetworkQueue) As Integer
		Return Me.networkQueue(CInt(queue)).Length
	End Function

	' Token: 0x06000604 RID: 1540 RVA: 0x0004A6D8 File Offset: 0x000488D8
	Public Sub SendSnapshots(ents As ListHashSet(Of Networkable))
		Using TimeWarning.[New]("SendSnapshots", 0)
			Dim count As Integer = ents.Values.Count
			Dim buffer As Networkable() = ents.Values.Buffer
			For i As Integer = 0 To count - 1
				Me.SnapshotQueue.Add(TryCast(buffer(i).handler, Global.BaseNetworkable))
			Next
		End Using
	End Sub

	' Token: 0x06000605 RID: 1541 RVA: 0x0004A74C File Offset: 0x0004894C
	Public Sub QueueUpdate(queue As Global.BasePlayer.NetworkQueue, ent As Global.BaseNetworkable)
		If Not Me.IsConnected Then
			Return
		End If
		If queue = Global.BasePlayer.NetworkQueue.Update Then
			Me.networkQueue(0).Add(ent)
			Return
		End If
		If queue <> Global.BasePlayer.NetworkQueue.UpdateDistance Then
			Return
		End If
		If Me.IsReceivingSnapshot Then
			Return
		End If
		If Me.networkQueue(1).Contains(ent) Then
			Return
		End If
		If Me.networkQueue(0).Contains(ent) Then
			Return
		End If
		Dim networkQueueList As Global.BasePlayer.NetworkQueueList = Me.networkQueue(1)
		If MyBase.Distance(TryCast(ent, Global.BaseEntity)) < 20F Then
			Me.QueueUpdate(Global.BasePlayer.NetworkQueue.Update, ent)
			Return
		End If
		networkQueueList.Add(ent)
	End Sub

	' Token: 0x06000606 RID: 1542 RVA: 0x0004A7D0 File Offset: 0x000489D0
	Public Sub SendEntityUpdate()
		Using TimeWarning.[New]("SendEntityUpdate", 0)
			Me.SendEntityUpdates(Me.SnapshotQueue)
			Me.SendEntityUpdates(Me.networkQueue(0))
			Me.SendEntityUpdates(Me.networkQueue(1))
		End Using
	End Sub

	' Token: 0x06000607 RID: 1543 RVA: 0x0004A830 File Offset: 0x00048A30
	Public Sub ClearEntityQueue(Optional group As Group = Nothing)
		Me.SnapshotQueue.Clear(group)
		Me.networkQueue(0).Clear(group)
		Me.networkQueue(1).Clear(group)
	End Sub

	' Token: 0x06000608 RID: 1544 RVA: 0x0004A85C File Offset: 0x00048A5C
	Private Sub SendEntityUpdates(queue As Global.BasePlayer.NetworkQueueList)
		If queue.queueInternal.Count = 0 Then
			Return
		End If
		Dim num As Integer = If(Me.IsReceivingSnapshot, ConVar.Server.updatebatchspawn, ConVar.Server.updatebatch)
		Dim list As List(Of Global.BaseNetworkable) = Facepunch.Pool.GetList(Of Global.BaseNetworkable)()
		Using TimeWarning.[New]("SendEntityUpdates.SendEntityUpdates", 0)
			Dim num2 As Integer = 0
			For Each baseNetworkable As Global.BaseNetworkable In queue.queueInternal
				Me.SendEntitySnapshot(baseNetworkable)
				list.Add(baseNetworkable)
				num2 += 1
				If num2 > num Then
					Exit For
				End If
			Next
		End Using
		If num > queue.queueInternal.Count Then
			queue.queueInternal.Clear()
		Else
			Using TimeWarning.[New]("SendEntityUpdates.Remove", 0)
				For i As Integer = 0 To list.Count - 1
					queue.queueInternal.Remove(list(i))
				Next
			End Using
		End If
		If queue.queueInternal.Count = 0 AndAlso queue.MaxLength > 2048 Then
			queue.queueInternal.Clear()
			queue.queueInternal = New HashSet(Of Global.BaseNetworkable)()
			queue.MaxLength = 0
		End If
		Facepunch.Pool.FreeList(Of Global.BaseNetworkable)(list)
	End Sub

	' Token: 0x06000609 RID: 1545 RVA: 0x0004A9B8 File Offset: 0x00048BB8
	Private Sub SendEntitySnapshot(ent As Global.BaseNetworkable)
		Using TimeWarning.[New]("SendEntitySnapshot", 0)
			If Not(ent Is Nothing) Then
				If ent.net IsNot Nothing Then
					If ent.ShouldNetworkTo(Me) Then
						Dim netWrite As NetWrite = Network.Net.sv.StartWrite()
						Dim connection As Network.Connection = Me.net.connection
						connection.validate.entityUpdates = connection.validate.entityUpdates + 1UI
						Dim saveInfo As Global.BaseNetworkable.SaveInfo = New Global.BaseNetworkable.SaveInfo() With { .forConnection = Me.net.connection, .forDisk = False }
						netWrite.PacketID(Message.Type.Entities)
						netWrite.UInt32(Me.net.connection.validate.entityUpdates)
						ent.ToStreamForNetwork(netWrite, saveInfo)
						netWrite.Send(New SendInfo(Me.net.connection))
					End If
				End If
			End If
		End Using
	End Sub

	' Token: 0x0600060A RID: 1546 RVA: 0x0004AAA0 File Offset: 0x00048CA0
	Public Function HasPlayerFlag(f As Global.BasePlayer.PlayerFlags) As Boolean
		Return(Me.playerFlags And f) = f
	End Function

	' Token: 0x170000A9 RID: 169
	' (get) Token: 0x0600060B RID: 1547 RVA: 0x0004AAAD File Offset: 0x00048CAD
	Public ReadOnly Property IsReceivingSnapshot As Boolean
		Get
			Return Me.HasPlayerFlag(Global.BasePlayer.PlayerFlags.ReceivingSnapshot)
		End Get
	End Property

	' Token: 0x170000AA RID: 170
	' (get) Token: 0x0600060C RID: 1548 RVA: 0x0004AAB6 File Offset: 0x00048CB6
	Public ReadOnly Property IsAdmin As Boolean
		Get
			Return Me.HasPlayerFlag(Global.BasePlayer.PlayerFlags.IsAdmin)
		End Get
	End Property

	' Token: 0x170000AB RID: 171
	' (get) Token: 0x0600060D RID: 1549 RVA: 0x0004AABF File Offset: 0x00048CBF
	Public ReadOnly Property IsDeveloper As Boolean
		Get
			Return Me.HasPlayerFlag(Global.BasePlayer.PlayerFlags.IsDeveloper)
		End Get
	End Property

	' Token: 0x170000AC RID: 172
	' (get) Token: 0x0600060E RID: 1550 RVA: 0x0004AACC File Offset: 0x00048CCC
	Public ReadOnly Property IsInCreativeMode As Boolean
		Get
			Return Creative.allUsers OrElse Me.HasPlayerFlag(Global.BasePlayer.PlayerFlags.CreativeMode)
		End Get
	End Property

	' Token: 0x170000AD RID: 173
	' (get) Token: 0x0600060F RID: 1551 RVA: 0x0004AAE2 File Offset: 0x00048CE2
	Public ReadOnly Property UnlockAllSkins As Boolean
		Get
			Return Me.IsDeveloper AndAlso MyBase.isServer AndAlso Me.net.connection.info.GetBool("client.unlock_all_skins", False)
		End Get
	End Property

	' Token: 0x170000AE RID: 174
	' (get) Token: 0x06000610 RID: 1552 RVA: 0x0004AB13 File Offset: 0x00048D13
	Public ReadOnly Property IsAiming As Boolean
		Get
			Return Me.HasPlayerFlag(Global.BasePlayer.PlayerFlags.Aiming)
		End Get
	End Property

	' Token: 0x170000AF RID: 175
	' (get) Token: 0x06000611 RID: 1553 RVA: 0x0004AB20 File Offset: 0x00048D20
	Public ReadOnly Property IsFlying As Boolean
		Get
			Return Me.modelState IsNot Nothing AndAlso Me.modelState.flying
		End Get
	End Property

	' Token: 0x170000B0 RID: 176
	' (get) Token: 0x06000612 RID: 1554 RVA: 0x0004AB37 File Offset: 0x00048D37
	Public ReadOnly Property IsConnected As Boolean
		Get
			Return MyBase.isServer AndAlso Network.Net.sv IsNot Nothing AndAlso Me.net IsNot Nothing AndAlso Me.net.connection IsNot Nothing
		End Get
	End Property

	' Token: 0x06000613 RID: 1555 RVA: 0x0004AB66 File Offset: 0x00048D66
	Public Sub SetPlayerFlag(f As Global.BasePlayer.PlayerFlags, b As Boolean)
		If b Then
			If Me.HasPlayerFlag(f) Then
				Return
			End If
			Me.playerFlags = Me.playerFlags Or f
		Else
			If Not Me.HasPlayerFlag(f) Then
				Return
			End If
			Me.playerFlags = Me.playerFlags And Not f
		End If
		MyBase.SendNetworkUpdate(Global.BasePlayer.NetworkQueue.Update)
	End Sub

	' Token: 0x06000614 RID: 1556 RVA: 0x0004ABA8 File Offset: 0x00048DA8
	Public Sub LightToggle(Optional mask As Boolean = True)
		Dim activeItem As Global.Item = Me.GetActiveItem()
		If activeItem IsNot Nothing Then
			Dim heldEntity As Global.BaseEntity = activeItem.GetHeldEntity()
			If heldEntity IsNot Nothing Then
				Dim component As Global.HeldEntity = heldEntity.GetComponent(Of Global.HeldEntity)()
				If component Then
					component.SendMessage("SetLightsOn", mask AndAlso Not component.LightsOn(), SendMessageOptions.DontRequireReceiver)
				End If
			End If
		End If
		For Each item As Global.Item In Me.inventory.containerWear.itemList
			Dim component2 As ItemModWearable = item.info.GetComponent(Of ItemModWearable)()
			If component2 AndAlso component2.emissive Then
				item.SetFlag(Global.Item.Flag.IsOn, mask AndAlso Not item.HasFlag(Global.Item.Flag.IsOn))
				item.MarkDirty()
			End If
		Next
		If Me.isMounted Then
			Me.GetMounted().LightToggle(Me)
		End If
	End Sub

	' Token: 0x170000B1 RID: 177
	' (get) Token: 0x06000615 RID: 1557 RVA: 0x0004AC9C File Offset: 0x00048E9C
	Public ReadOnly Property IsInTutorial As Boolean
		Get
			Return Me.HasPlayerFlag(Global.BasePlayer.PlayerFlags.IsInTutorial)
		End Get
	End Property

	' Token: 0x170000B2 RID: 178
	' (get) Token: 0x06000616 RID: 1558 RVA: 0x0004ACA9 File Offset: 0x00048EA9
	Public ReadOnly Property IsRestrained As Boolean
		Get
			Return Me.IsAlive() AndAlso Me.HasPlayerFlag(Global.BasePlayer.PlayerFlags.IsRestrained)
		End Get
	End Property

	' Token: 0x170000B3 RID: 179
	' (get) Token: 0x06000617 RID: 1559 RVA: 0x0004ACC0 File Offset: 0x00048EC0
	Public ReadOnly Property IsRestrainedOrSurrendering As Boolean
		Get
			Return Me.IsRestrained OrElse Me.CurrentGestureIsSurrendering
		End Get
	End Property

	' Token: 0x170000B4 RID: 180
	' (get) Token: 0x06000618 RID: 1560 RVA: 0x0004ACD2 File Offset: 0x00048ED2
	Public ReadOnly Property InGesture As Boolean
		Get
			Return Me.currentGesture IsNot Nothing AndAlso (Me.gestureFinishedTime > 0F OrElse Me.currentGesture.animationType = GestureConfig.AnimationType.[Loop])
		End Get
	End Property

	' Token: 0x170000B5 RID: 181
	' (get) Token: 0x06000619 RID: 1561 RVA: 0x0004AD06 File Offset: 0x00048F06
	Private ReadOnly Property CurrentGestureBlocksMovement As Boolean
		Get
			Return Me.InGesture AndAlso Me.currentGesture.movementMode = GestureConfig.MovementCapabilities.NoMovement
		End Get
	End Property

	' Token: 0x170000B6 RID: 182
	' (get) Token: 0x0600061A RID: 1562 RVA: 0x0004AD20 File Offset: 0x00048F20
	Public ReadOnly Property CurrentGestureIsDance As Boolean
		Get
			Return Me.InGesture AndAlso Me.currentGesture.actionType = GestureConfig.GestureActionType.DanceAchievement
		End Get
	End Property

	' Token: 0x170000B7 RID: 183
	' (get) Token: 0x0600061B RID: 1563 RVA: 0x0004AD3A File Offset: 0x00048F3A
	Public ReadOnly Property CurrentGestureIsFullBody As Boolean
		Get
			Return Me.InGesture AndAlso Me.currentGesture.playerModelLayer = GestureConfig.PlayerModelLayer.FullBody
		End Get
	End Property

	' Token: 0x170000B8 RID: 184
	' (get) Token: 0x0600061C RID: 1564 RVA: 0x0004AD54 File Offset: 0x00048F54
	Public ReadOnly Property CurrentGestureIsUpperBody As Boolean
		Get
			Return Me.InGesture AndAlso Me.currentGesture.playerModelLayer = GestureConfig.PlayerModelLayer.UpperBody
		End Get
	End Property

	' Token: 0x170000B9 RID: 185
	' (get) Token: 0x0600061D RID: 1565 RVA: 0x0004AD6E File Offset: 0x00048F6E
	Public ReadOnly Property CurrentGestureIsSurrendering As Boolean
		Get
			Return Me.InGesture AndAlso Me.currentGesture.actionType = GestureConfig.GestureActionType.Surrender
		End Get
	End Property

	' Token: 0x170000BA RID: 186
	' (get) Token: 0x0600061E RID: 1566 RVA: 0x0004AD88 File Offset: 0x00048F88
	Private ReadOnly Property InGestureCancelCooldown As Boolean
		Get
			Return Me.blockHeldInputTimer < 0.5F
		End Get
	End Property

	' Token: 0x0600061F RID: 1567 RVA: 0x0004AD9C File Offset: 0x00048F9C
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.FromOwner()>
	<Global.BaseEntity.RPC_Server.CallsPerSecond(1UL)>
	Private Sub Server_StartGesture(msg As Global.BaseEntity.RPCMessage)
		If Me.IsGestureBlocked() Then
			Return
		End If
		Dim id As UInteger = msg.read.UInt32()
		If Me.gestureList Is Nothing Then
			Return
		End If
		Dim toPlay As GestureConfig = Me.gestureList.IdToGesture(id)
		Me.Server_StartGesture(toPlay, Global.BasePlayer.GestureStartSource.Player)
	End Sub

	' Token: 0x06000620 RID: 1568 RVA: 0x0004ADE4 File Offset: 0x00048FE4
	Public Sub Server_StartGesture(gestureId As UInteger)
		If Me.gestureList Is Nothing Then
			Return
		End If
		Dim toPlay As GestureConfig = Me.gestureList.IdToGesture(gestureId)
		Me.Server_StartGesture(toPlay, Global.BasePlayer.GestureStartSource.Player)
	End Sub

	' Token: 0x06000621 RID: 1569 RVA: 0x0004AE18 File Offset: 0x00049018
	Public Sub Server_StartGesture(toPlay As GestureConfig, Optional startSource As Global.BasePlayer.GestureStartSource = Global.BasePlayer.GestureStartSource.Player)
		If toPlay IsNot Nothing AndAlso toPlay.hideInWheel AndAlso startSource = Global.BasePlayer.GestureStartSource.Player AndAlso Not ConVar.Server.cinematic Then
			Return
		End If
		If toPlay IsNot Nothing AndAlso toPlay.IsOwnedBy(Me) AndAlso toPlay.CanBeUsedBy(Me) Then
			If toPlay.animationType = GestureConfig.AnimationType.OneShot Then
				MyBase.Invoke(AddressOf Me.TimeoutGestureServer, toPlay.duration)
			ElseIf toPlay.animationType = GestureConfig.AnimationType.[Loop] Then
				MyBase.InvokeRepeating(AddressOf Me.MonitorLoopingGesture, 0F, 0F)
			End If
			MyBase.ClientRPC(Of UInteger)(RpcTarget.NetworkGroup("Client_StartGesture"), toPlay.gestureId)
			Me.gestureFinishedTime = toPlay.duration
			Me.currentGesture = toPlay
			Select Case toPlay.actionType
				Case GestureConfig.GestureActionType.ShowNameTag
					If GameInfo.HasAchievements Then
						Dim val As Integer = Me.CountWaveTargets(MyBase.transform.position, 4F, 0.6F, Me.eyes.HeadForward(), Me.recentWaveTargets, 5)
						Me.stats.Add("waved_at_players", val, Global.Stats.Steam)
						Me.stats.Save(True)
					End If
				Case GestureConfig.GestureActionType.DanceAchievement
					Dim triggerDanceAchievement As TriggerDanceAchievement = MyBase.FindTrigger(Of TriggerDanceAchievement)()
					If triggerDanceAchievement IsNot Nothing Then
						triggerDanceAchievement.NotifyDanceStarted()
					End If
				Case GestureConfig.GestureActionType.Surrender
					Me.inventory.SetLockedByRestraint(True)
			End Select
			If toPlay.animationType = GestureConfig.AnimationType.[Loop] Then
				MyBase.SendNetworkUpdate(Global.BasePlayer.NetworkQueue.Update)
			End If
		End If
	End Sub

	' Token: 0x06000622 RID: 1570 RVA: 0x0004AF81 File Offset: 0x00049181
	Private Sub TimeoutGestureServer()
		Me.currentGesture = Nothing
	End Sub

	' Token: 0x06000623 RID: 1571 RVA: 0x0004AF8C File Offset: 0x0004918C
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.FromOwner()>
	<Global.BaseEntity.RPC_Server.CallsPerSecond(10UL)>
	Public Sub Server_CancelGesture()
		If Me.currentGesture IsNot Nothing AndAlso Me.currentGesture.actionType = GestureConfig.GestureActionType.Surrender Then
			Dim handcuffs As Handcuffs = TryCast(Me.GetHeldEntity(), Handcuffs)
			If handcuffs Is Nothing OrElse Not handcuffs.Locked Then
				Me.inventory.SetLockedByRestraint(False)
			End If
		End If
		Me.currentGesture = Nothing
		Me.blockHeldInputTimer = 0F
		MyBase.ClientRPC(RpcTarget.NetworkGroup("Client_RemoteCancelledGesture"))
		MyBase.CancelInvoke(AddressOf Me.MonitorLoopingGesture)
		MyBase.CancelInvoke(AddressOf Me.TimeoutGestureServer)
	End Sub

	' Token: 0x06000624 RID: 1572 RVA: 0x0004B02C File Offset: 0x0004922C
	Private Sub MonitorLoopingGesture()
		Dim flag As Boolean = Me.currentGesture IsNot Nothing AndAlso Me.currentGesture.canDuckDuringGesture
		If Me.modelState Is Nothing OrElse (Not flag AndAlso Me.modelState.ducked) OrElse (Me.modelState.sleeping OrElse Me.IsWounded() OrElse Me.IsSwimming() OrElse Me.IsDead() OrElse (Me.isMounted AndAlso Me.GetMounted().allowedGestures = BaseMountable.MountGestureType.UpperBody AndAlso Me.CurrentGestureIsUpperBody)) OrElse (Me.isMounted AndAlso Me.GetMounted().allowedGestures = BaseMountable.MountGestureType.None) Then
			Me.Server_CancelGesture()
		End If
	End Sub

	' Token: 0x06000625 RID: 1573 RVA: 0x0004B0CC File Offset: 0x000492CC
	Private Sub NotifyGesturesNewItemEquipped()
		If Me.InGesture Then
			Me.Server_CancelGesture()
		End If
	End Sub

	' Token: 0x06000626 RID: 1574 RVA: 0x0004B0DC File Offset: 0x000492DC
	Public Function CountWaveTargets(position As Vector3, distance As Single, minimumDot As Single, forward As Vector3, workingList As HashSet(Of NetworkableId), maxCount As Integer) As Integer
		Dim CS$<>8__locals1 As Global.BasePlayer.<>c__DisplayClass118_0
		CS$<>8__locals1.<>4__this = Me
		CS$<>8__locals1.position = position
		CS$<>8__locals1.forward = forward
		CS$<>8__locals1.minimumDot = minimumDot
		CS$<>8__locals1.workingList = workingList
		CS$<>8__locals1.sqrDistance = distance * distance
		Dim group As Group = Me.net.group
		If group Is Nothing Then
			Return 0
		End If
		Dim subscribers As List(Of Network.Connection) = group.subscribers
		Dim num As Integer = 0
		For i As Integer = 0 To subscribers.Count - 1
			Dim connection As Network.Connection = subscribers(i)
			If connection.active Then
				Dim basePlayer As Global.BasePlayer = TryCast(connection.player, Global.BasePlayer)
				If Me.<CountWaveTargets>g__CheckPlayer|118_0(basePlayer, CS$<>8__locals1) Then
					CS$<>8__locals1.workingList.Add(basePlayer.net.ID)
					num += 1
					If num >= maxCount Then
						Exit For
					End If
				End If
			End If
		Next
		Return num
	End Function

	' Token: 0x06000627 RID: 1575 RVA: 0x0004B19C File Offset: 0x0004939C
	Private Function IsGestureBlocked() As Boolean
		If Me.isMounted AndAlso Me.GetMounted().allowedGestures = BaseMountable.MountGestureType.None Then
			Return True
		End If
		If Me.GetHeldEntity() AndAlso Me.GetHeldEntity().BlocksGestures() Then
			Return True
		End If
		Dim flag As Boolean = Me.currentGesture IsNot Nothing
		If flag AndAlso Me.currentGesture.gestureType = GestureConfig.GestureType.Cinematic Then
			flag = False
		End If
		Return Me.IsWounded() OrElse flag OrElse Me.IsDead() OrElse Me.IsSleeping() OrElse Me.IsRestrained
	End Function

	' Token: 0x170000BB RID: 187
	' (get) Token: 0x06000628 RID: 1576 RVA: 0x0004B21E File Offset: 0x0004941E
	Public ReadOnly Property Team As Global.RelationshipManager.PlayerTeam
		Get
			If Global.RelationshipManager.ServerInstance Is Nothing Then
				Return Nothing
			End If
			Return Global.RelationshipManager.ServerInstance.FindTeam(Me.currentTeam)
		End Get
	End Property

	' Token: 0x06000629 RID: 1577 RVA: 0x0004B23F File Offset: 0x0004943F
	Public Sub DelayedTeamUpdate()
		Me.UpdateTeam(Me.currentTeam)
	End Sub

	' Token: 0x0600062A RID: 1578 RVA: 0x0004B24D File Offset: 0x0004944D
	Public Sub TeamUpdate()
		Me.TeamUpdate(False)
	End Sub

	' Token: 0x0600062B RID: 1579 RVA: 0x0004B258 File Offset: 0x00049458
	Public Sub TeamUpdate(fullTeamUpdate As Boolean)
		If Not Global.RelationshipManager.TeamsEnabled() Then
			Return
		End If
		If Me.IsConnected AndAlso Me.currentTeam <> 0UL Then
			Dim playerTeam As Global.RelationshipManager.PlayerTeam = Global.RelationshipManager.ServerInstance.FindTeam(Me.currentTeam)
			If playerTeam Is Nothing Then
				Return
			End If
			Dim num As Integer = 0
			Dim num2 As Integer = 0
			Using playerTeam2 As PlayerTeam = Facepunch.Pool.[Get](Of PlayerTeam)()
				playerTeam2.teamLeader = playerTeam.teamLeader
				playerTeam2.teamID = playerTeam.teamID
				playerTeam2.teamName = playerTeam.teamName
				playerTeam2.members = Facepunch.Pool.GetList(Of PlayerTeam.TeamMember)()
				playerTeam2.teamLifetime = playerTeam.teamLifetime
				playerTeam2.teamPings = Facepunch.Pool.GetList(Of MapNote)()
				For Each playerID As ULong In playerTeam.members
					Dim basePlayer As Global.BasePlayer = Global.RelationshipManager.FindByID(playerID)
					If Not basePlayer OrElse Not basePlayer.IsInTutorial Then
						Dim teamMember As PlayerTeam.TeamMember = Facepunch.Pool.[Get](Of PlayerTeam.TeamMember)()
						teamMember.displayName = If((basePlayer IsNot Nothing), basePlayer.displayName, (If(SingletonComponent(Of ServerMgr).Instance.persistance.GetPlayerName(playerID), "DEAD")))
						teamMember.healthFraction = If((basePlayer IsNot Nothing AndAlso basePlayer.IsAlive()), basePlayer.healthFraction, 0F)
						teamMember.position = If((basePlayer IsNot Nothing), basePlayer.transform.position, Vector3.zero)
						teamMember.online = (basePlayer IsNot Nothing AndAlso Not basePlayer.IsSleeping())
						teamMember.wounded = (basePlayer IsNot Nothing AndAlso basePlayer.IsWounded())
						If(Not Me.sentInstrumentTeamAchievement OrElse Not Me.sentSummerTeamAchievement) AndAlso basePlayer IsNot Nothing Then
							If basePlayer.GetHeldEntity() AndAlso basePlayer.GetHeldEntity().IsInstrument() Then
								num += 1
							End If
							If basePlayer.isMounted Then
								If basePlayer.GetMounted().IsInstrument() Then
									num += 1
								End If
								If basePlayer.GetMounted().IsSummerDlcVehicle Then
									num2 += 1
								End If
							End If
							If num >= 4 AndAlso Not Me.sentInstrumentTeamAchievement Then
								Me.GiveAchievement("TEAM_INSTRUMENTS", False)
								Me.sentInstrumentTeamAchievement = True
							End If
							If num2 >= 4 Then
								Me.GiveAchievement("SUMMER_INFLATABLE", False)
								Me.sentSummerTeamAchievement = True
							End If
						End If
						teamMember.userID = playerID
						playerTeam2.members.Add(teamMember)
						If basePlayer IsNot Nothing Then
							If basePlayer.State.pings IsNot Nothing AndAlso basePlayer.State.pings.Count > 0 AndAlso basePlayer IsNot Me Then
								playerTeam2.teamPings.AddRange(basePlayer.State.pings)
							End If
							If fullTeamUpdate AndAlso basePlayer IsNot Me Then
								basePlayer.TeamUpdate(False)
							End If
						End If
					End If
				Next
				playerTeam2.leaderMapNotes = Facepunch.Pool.GetList(Of MapNote)()
				Dim playerState As PlayerState = SingletonComponent(Of ServerMgr).Instance.playerStateManager.[Get](playerTeam.teamLeader)
				If If((playerState IsNot Nothing), playerState.pointsOfInterest, Nothing) IsNot Nothing Then
					For Each item As MapNote In playerState.pointsOfInterest
						playerTeam2.leaderMapNotes.Add(item)
					Next
				End If
				MyBase.ClientRPC(Of PlayerTeam)(RpcTarget.PlayerAndSpectators("CLIENT_ReceiveTeamInfo", Me), playerTeam2)
				If playerTeam2.leaderMapNotes IsNot Nothing Then
					playerTeam2.leaderMapNotes.Clear()
				End If
				If playerTeam2.teamPings IsNot Nothing Then
					playerTeam2.teamPings.Clear()
				End If
				Dim basePlayer2 As Global.BasePlayer = Global.BasePlayer.FindByID(playerTeam.teamLeader)
				If fullTeamUpdate AndAlso basePlayer2 IsNot Nothing AndAlso basePlayer2 IsNot Me Then
					basePlayer2.TeamUpdate(False)
				End If
			End Using
		End If
	End Sub

	' Token: 0x0600062C RID: 1580 RVA: 0x0004B648 File Offset: 0x00049848
	Public Sub UpdateTeam(newTeam As ULong)
		Me.currentTeam = newTeam
		MyBase.SendNetworkUpdate(Global.BasePlayer.NetworkQueue.Update)
		If Global.RelationshipManager.ServerInstance.FindTeam(newTeam) Is Nothing Then
			Me.ClearTeam()
			Return
		End If
		Me.TeamUpdate()
	End Sub

	' Token: 0x0600062D RID: 1581 RVA: 0x0004B672 File Offset: 0x00049872
	Public Sub ClearTeam()
		Me.currentTeam = 0UL
		MyBase.ClientRPC(RpcTarget.PlayerAndSpectators("CLIENT_ClearTeam", Me))
		MyBase.SendNetworkUpdate(Global.BasePlayer.NetworkQueue.Update)
	End Sub

	' Token: 0x0600062E RID: 1582 RVA: 0x0004B694 File Offset: 0x00049894
	Public Sub ClearPendingInvite()
		MyBase.ClientRPC(Of String, Integer)(RpcTarget.Player("CLIENT_PendingInvite", Me), "", 0)
	End Sub

	' Token: 0x0600062F RID: 1583 RVA: 0x0004B6B0 File Offset: 0x000498B0
	Public Function GetHeldEntity() As Global.HeldEntity
		If Not MyBase.isServer Then
			Return Nothing
		End If
		Dim activeItem As Global.Item = Me.GetActiveItem()
		If activeItem Is Nothing Then
			Return Nothing
		End If
		Return TryCast(activeItem.GetHeldEntity(), Global.HeldEntity)
	End Function

	' Token: 0x06000630 RID: 1584 RVA: 0x0004B6E0 File Offset: 0x000498E0
	Public Function IsHoldingEntity(Of T)() As Boolean
		Dim heldEntity As Global.HeldEntity = Me.GetHeldEntity()
		Return Not(heldEntity Is Nothing) AndAlso TypeOf heldEntity Is T
	End Function

	' Token: 0x06000631 RID: 1585 RVA: 0x0004B708 File Offset: 0x00049908
	Public Function IsHostileItem(item As Global.Item) As Boolean
		If Not item.info.isHoldable Then
			Return False
		End If
		Dim component As ItemModEntity = item.info.GetComponent(Of ItemModEntity)()
		If component Is Nothing Then
			Return False
		End If
		Dim gameObject As GameObject = component.entityPrefab.[Get]()
		If gameObject Is Nothing Then
			Return False
		End If
		Dim component2 As AttackEntity = gameObject.GetComponent(Of AttackEntity)()
		Return Not(component2 Is Nothing) AndAlso component2.hostile
	End Function

	' Token: 0x06000632 RID: 1586 RVA: 0x0004B76A File Offset: 0x0004996A
	Public Function IsItemHoldRestricted(item As Global.Item) As Boolean
		Return Not Me.IsNpc AndAlso (Me.InSafeZone() AndAlso item IsNot Nothing AndAlso Me.IsHostileItem(item))
	End Function

	' Token: 0x170000BC RID: 188
	' (get) Token: 0x06000633 RID: 1587 RVA: 0x0004B78D File Offset: 0x0004998D
	' (set) Token: 0x06000634 RID: 1588 RVA: 0x0004B79A File Offset: 0x0004999A
	Public Property ServerCurrentDeathNote As MapNote
		Get
			Return Me.State.deathMarker
		End Get
		Set(value As MapNote)
			Me.State.deathMarker = value
		End Set
	End Property

	' Token: 0x06000635 RID: 1589 RVA: 0x0004B7A8 File Offset: 0x000499A8
	Public Sub ClearDeathMarker(Optional sendToClient As Boolean = False)
		If Me.IsNpc Then
			Return
		End If
		If Me.ServerCurrentDeathNote IsNot Nothing Then
			Facepunch.Pool.Free(Of MapNote)(Me.State.deathMarker)
		End If
		Me.DirtyPlayerState()
		If sendToClient Then
			Me.SendMarkersToClient()
		End If
	End Sub

	' Token: 0x06000636 RID: 1590 RVA: 0x0004B7DC File Offset: 0x000499DC
	Public Sub Server_LogDeathMarker(position As Vector3)
		If Me.IsNpc Then
			Return
		End If
		If Me.ServerCurrentDeathNote Is Nothing Then
			Me.ServerCurrentDeathNote = Facepunch.Pool.[Get](Of MapNote)()
			Me.ServerCurrentDeathNote.noteType = 0
		End If
		Me.ServerCurrentDeathNote.worldPosition = position
		MyBase.ClientRPC(Of MapNote)(RpcTarget.Player("Client_AddNewDeathMarker", Me), Me.ServerCurrentDeathNote)
		Me.DirtyPlayerState()
	End Sub

	' Token: 0x06000637 RID: 1591 RVA: 0x0004B83C File Offset: 0x00049A3C
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.FromOwner()>
	<Global.BaseEntity.RPC_Server.CallsPerSecond(8UL)>
	Public Sub Server_AddMarker(msg As Global.BaseEntity.RPCMessage)
		If Me.State.pointsOfInterest Is Nothing Then
			Me.State.pointsOfInterest = Facepunch.Pool.GetList(Of MapNote)()
		End If
		If Me.State.pointsOfInterest.Count >= ConVar.Server.maximumMapMarkers Then
			msg.player.ShowToast(GameTip.Styles.Blue_Short, Global.BasePlayer.MarkerLimitPhrase, New String() { ConVar.Server.maximumMapMarkers.ToString() })
			Return
		End If
		Dim mapNote As MapNote = MapNote.Deserialize(msg.read)
		Me.ValidateMapNote(mapNote)
		mapNote.colourIndex = Me.FindUnusedPointOfInterestColour()
		Me.State.pointsOfInterest.Add(mapNote)
		Me.DirtyPlayerState()
		Me.SendMarkersToClient()
		Me.TeamUpdate()
	End Sub

	' Token: 0x06000638 RID: 1592 RVA: 0x0004B8E4 File Offset: 0x00049AE4
	Private Function FindUnusedPointOfInterestColour() As Integer
		If Me.State.pointsOfInterest Is Nothing Then
			Return 0
		End If
		Dim num As Integer = 0
		For i As Integer = 0 To 6 - 1
			If Me.<FindUnusedPointOfInterestColour>g__HasColour|149_0(num) Then
				num += 1
			End If
		Next
		Return num
	End Function

	' Token: 0x06000639 RID: 1593 RVA: 0x0004B91C File Offset: 0x00049B1C
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.FromOwner()>
	<Global.BaseEntity.RPC_Server.CallsPerSecond(1UL)>
	Public Sub Server_UpdateMarker(msg As Global.BaseEntity.RPCMessage)
		If Me.State.pointsOfInterest Is Nothing Then
			Me.State.pointsOfInterest = Facepunch.Pool.GetList(Of MapNote)()
		End If
		Dim num As Integer = msg.read.Int32()
		If Me.State.pointsOfInterest.Count <= num Then
			Return
		End If
		Using mapNote As MapNote = MapNote.Deserialize(msg.read)
			Me.ValidateMapNote(mapNote)
			mapNote.CopyTo(Me.State.pointsOfInterest(num))
			Me.DirtyPlayerState()
			Me.SendMarkersToClient()
			Me.TeamUpdate()
		End Using
	End Sub

	' Token: 0x0600063A RID: 1594 RVA: 0x0004B9C0 File Offset: 0x00049BC0
	Private Sub ValidateMapNote(n As MapNote)
		If n.label IsNot Nothing Then
			n.label = n.label.Truncate(10, Nothing).ToUpperInvariant()
		End If
	End Sub

	' Token: 0x0600063B RID: 1595 RVA: 0x0004B9E4 File Offset: 0x00049BE4
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.FromOwner()>
	<Global.BaseEntity.RPC_Server.CallsPerSecond(10UL)>
	Public Sub Server_RemovePointOfInterest(msg As Global.BaseEntity.RPCMessage)
		Dim num As Integer = msg.read.Int32()
		If Me.State.pointsOfInterest IsNot Nothing AndAlso Me.State.pointsOfInterest.Count > num AndAlso num >= 0 Then
			Me.State.pointsOfInterest(num).Dispose()
			Me.State.pointsOfInterest.RemoveAt(num)
			Me.DirtyPlayerState()
			Me.SendMarkersToClient()
			Me.TeamUpdate()
		End If
	End Sub

	' Token: 0x0600063C RID: 1596 RVA: 0x0004BA5A File Offset: 0x00049C5A
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.FromOwner()>
	<Global.BaseEntity.RPC_Server.CallsPerSecond(1UL)>
	Public Sub Server_RequestMarkers(msg As Global.BaseEntity.RPCMessage)
		Me.SendMarkersToClient()
	End Sub

	' Token: 0x0600063D RID: 1597 RVA: 0x0004BA64 File Offset: 0x00049C64
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.FromOwner()>
	<Global.BaseEntity.RPC_Server.CallsPerSecond(1UL)>
	Public Sub Server_ClearMapMarkers(msg As Global.BaseEntity.RPCMessage)
		Dim serverCurrentDeathNote As MapNote = Me.ServerCurrentDeathNote
		If serverCurrentDeathNote IsNot Nothing Then
			serverCurrentDeathNote.Dispose()
		End If
		Me.ServerCurrentDeathNote = Nothing
		If Me.State.pointsOfInterest IsNot Nothing Then
			For Each mapNote As MapNote In Me.State.pointsOfInterest
				If mapNote IsNot Nothing Then
					mapNote.Dispose()
				End If
			Next
			Me.State.pointsOfInterest.Clear()
		End If
		Me.DirtyPlayerState()
		Me.TeamUpdate()
	End Sub

	' Token: 0x0600063E RID: 1598 RVA: 0x0004BB00 File Offset: 0x00049D00
	Private Sub SendMarkersToClient()
		Using mapNoteList As MapNoteList = Facepunch.Pool.[Get](Of MapNoteList)()
			mapNoteList.notes = Facepunch.Pool.GetList(Of MapNote)()
			If Me.ServerCurrentDeathNote IsNot Nothing Then
				mapNoteList.notes.Add(Me.ServerCurrentDeathNote)
			End If
			If Me.State.pointsOfInterest IsNot Nothing Then
				mapNoteList.notes.AddRange(Me.State.pointsOfInterest)
			End If
			MyBase.ClientRPC(Of MapNoteList)(RpcTarget.Player("Client_ReceiveMarkers", Me), mapNoteList)
			mapNoteList.notes.Clear()
		End Using
	End Sub

	' Token: 0x0600063F RID: 1599 RVA: 0x0004BB94 File Offset: 0x00049D94
	Public Function HasAttemptedMission(missionID As UInteger) As Boolean
		Using enumerator As List(Of BaseMission.MissionInstance).Enumerator = Me.missions.GetEnumerator()
			While enumerator.MoveNext()
				If enumerator.Current.missionID = missionID Then
					Return True
				End If
			End While
		End Using
		Return False
	End Function

	' Token: 0x06000640 RID: 1600 RVA: 0x0004BBF0 File Offset: 0x00049DF0
	Public Function CanAcceptMission(mission As BaseMission) As Boolean
		Return Me.CanAcceptMission(mission.id)
	End Function

	' Token: 0x06000641 RID: 1601 RVA: 0x0004BC00 File Offset: 0x00049E00
	Public Function CanAcceptMission(missionID As UInteger) As Boolean
		If Me.HasActiveMission() Then
			Return False
		End If
		If Not BaseMission.missionsenabled Then
			Return False
		End If
		Dim fromID As BaseMission = MissionManifest.GetFromID(missionID)
		If fromID Is Nothing Then
			Debug.LogError("MISSION NOT FOUND IN MANIFEST, ID :" + missionID.ToString())
			Return False
		End If
		If fromID.acceptDependancies IsNot Nothing AndAlso fromID.acceptDependancies.Length <> 0 Then
			For Each missionDependancy As BaseMission.MissionDependancy In fromID.acceptDependancies
				If Not missionDependancy.everAttempted Then
					Dim flag As Boolean = False
					For Each missionInstance As BaseMission.MissionInstance In Me.missions
						If missionInstance.missionID = missionDependancy.targetMissionID AndAlso missionInstance.status = missionDependancy.targetMissionDesiredStatus Then
							flag = True
						End If
					Next
					If Not flag Then
						Return False
					End If
				End If
			Next
		End If
		If Me.IsMissionActive(missionID) Then
			Return False
		End If
		If fromID.isRepeatable Then
			Dim flag2 As Boolean = Me.HasCompletedMission(missionID)
			Dim flag3 As Boolean = Me.HasFailedMission(missionID)
			If flag2 AndAlso fromID.repeatDelaySecondsSuccess <= -1 Then
				Return False
			End If
			If flag3 AndAlso fromID.repeatDelaySecondsFailed <= -1 Then
				Return False
			End If
			For Each missionInstance2 As BaseMission.MissionInstance In Me.missions
				If missionInstance2.missionID = missionID Then
					Dim num As Single = 0F
					If missionInstance2.status = BaseMission.MissionStatus.Completed Then
						num = CSng(fromID.repeatDelaySecondsSuccess)
					ElseIf missionInstance2.status = BaseMission.MissionStatus.Failed Then
						num = CSng(fromID.repeatDelaySecondsFailed)
					End If
					Dim endTime As Single = missionInstance2.endTime
					If UnityEngine.Time.time - endTime < num Then
						Return False
					End If
				End If
			Next
		End If
		Dim positionGenerators As BaseMission.PositionGenerator() = fromID.positionGenerators
		For i As Integer = 0 To positionGenerators.Length - 1
			If Not positionGenerators(i).Validate(Me, fromID) Then
				Return False
			End If
		Next
		Return True
	End Function

	' Token: 0x06000642 RID: 1602 RVA: 0x0004BDE4 File Offset: 0x00049FE4
	Public Function IsMissionActive(missionID As UInteger) As Boolean
		For Each missionInstance As BaseMission.MissionInstance In Me.missions
			If missionInstance.missionID = missionID AndAlso (missionInstance.status = BaseMission.MissionStatus.Active OrElse missionInstance.status = BaseMission.MissionStatus.Accomplished) Then
				Return True
			End If
		Next
		Return False
	End Function

	' Token: 0x06000643 RID: 1603 RVA: 0x0004BE54 File Offset: 0x0004A054
	Public Function HasCompletedMission(missionID As UInteger) As Boolean
		For Each missionInstance As BaseMission.MissionInstance In Me.missions
			If missionInstance.missionID = missionID AndAlso missionInstance.status = BaseMission.MissionStatus.Completed Then
				Return True
			End If
		Next
		Return False
	End Function

	' Token: 0x06000644 RID: 1604 RVA: 0x0004BEBC File Offset: 0x0004A0BC
	Public Function HasFailedMission(missionID As UInteger) As Boolean
		For Each missionInstance As BaseMission.MissionInstance In Me.missions
			If missionInstance.missionID = missionID AndAlso missionInstance.status = BaseMission.MissionStatus.Failed Then
				Return True
			End If
		Next
		Return False
	End Function

	' Token: 0x06000645 RID: 1605 RVA: 0x0004BF24 File Offset: 0x0004A124
	Private Sub WipeMissions()
		If Me.missions.Count > 0 Then
			For i As Integer = Me.missions.Count - 1 To 0 Step -1
				Dim missionInstance As BaseMission.MissionInstance = Me.missions(i)
				If missionInstance IsNot Nothing Then
					missionInstance.GetMission().MissionFailed(missionInstance, Me, BaseMission.MissionFailReason.ResetPlayerState)
					Facepunch.Pool.Free(Of BaseMission.MissionInstance)(missionInstance)
				End If
			Next
		End If
		Me.missions.Clear()
		Me.SetActiveMission(-1)
		Me.MissionDirty(True)
	End Sub

	' Token: 0x06000646 RID: 1606 RVA: 0x0004BF98 File Offset: 0x0004A198
	Public Sub AbandonActiveMission()
		If Not Me.HasActiveMission() Then
			Return
		End If
		Dim activeMission As Integer = Me.GetActiveMission()
		If activeMission <> -1 AndAlso activeMission < Me.missions.Count Then
			Dim missionInstance As BaseMission.MissionInstance = Me.missions(activeMission)
			missionInstance.GetMission().MissionFailed(missionInstance, Me, BaseMission.MissionFailReason.Abandon)
		End If
	End Sub

	' Token: 0x06000647 RID: 1607 RVA: 0x0004BFE4 File Offset: 0x0004A1E4
	Public Sub ThinkMissions(delta As Single)
		If Not BaseMission.missionsenabled Then
			Return
		End If
		If Me.timeSinceMissionThink < Me.thinkEvery Then
			Me.timeSinceMissionThink += delta
			Return
		End If
		For Each missionInstance As BaseMission.MissionInstance In Me.missions
			missionInstance.Think(Me, Me.timeSinceMissionThink)
		Next
		Me.timeSinceMissionThink = 0F
	End Sub

	' Token: 0x06000648 RID: 1608 RVA: 0x0004C06C File Offset: 0x0004A26C
	Public Sub MissionDirty(Optional shouldSendNetworkUpdate As Boolean = True)
		If Not BaseMission.missionsenabled Then
			Return
		End If
		Me.State.missions = Me.SaveMissions()
		Me.DirtyPlayerState()
		If shouldSendNetworkUpdate Then
			MyBase.SendNetworkUpdate(Global.BasePlayer.NetworkQueue.Update)
		End If
	End Sub

	' Token: 0x06000649 RID: 1609 RVA: 0x0004C098 File Offset: 0x0004A298
	Public Sub ProcessMissionEvent(type As BaseMission.MissionEventType, identifier As UInteger, amount As Single)
		Me.ProcessMissionEvent(type, New BaseMission.MissionEventPayload() With { .UintIdentifier = identifier }, amount)
	End Sub

	' Token: 0x0600064A RID: 1610 RVA: 0x0004C0C0 File Offset: 0x0004A2C0
	Public Sub ProcessMissionEvent(type As BaseMission.MissionEventType, identifier As UInteger, amount As Single, worldPos As Vector3)
		Me.ProcessMissionEvent(type, New BaseMission.MissionEventPayload() With { .UintIdentifier = identifier, .WorldPosition = worldPos }, amount)
	End Sub

	' Token: 0x0600064B RID: 1611 RVA: 0x0004C0F0 File Offset: 0x0004A2F0
	Public Sub ProcessMissionEvent(type As BaseMission.MissionEventType, identifier As Integer, amount As Single)
		Me.ProcessMissionEvent(type, New BaseMission.MissionEventPayload() With { .IntIdentifier = identifier }, amount)
	End Sub

	' Token: 0x0600064C RID: 1612 RVA: 0x0004C118 File Offset: 0x0004A318
	Public Sub ProcessMissionEvent(type As BaseMission.MissionEventType, identifier As NetworkableId, amount As Single)
		Me.ProcessMissionEvent(type, New BaseMission.MissionEventPayload() With { .NetworkIdentifier = identifier }, amount)
	End Sub

	' Token: 0x0600064D RID: 1613 RVA: 0x0004C140 File Offset: 0x0004A340
	Public Sub ProcessMissionEvent(type As BaseMission.MissionEventType, payload As BaseMission.MissionEventPayload, amount As Single)
		If Not BaseMission.missionsenabled Then
			Return
		End If
		For Each missionInstance As BaseMission.MissionInstance In Me.missions
			missionInstance.ProcessMissionEvent(Me, type, payload, amount)
		Next
	End Sub

	' Token: 0x0600064E RID: 1614 RVA: 0x0004C19C File Offset: 0x0004A39C
	Private Sub AssignFollowUpMission()
		If Me.followupMission IsNot Nothing AndAlso Me.followupMissionProvider IsNot Nothing Then
			BaseMission.AssignMission(Me, Me.followupMissionProvider, Me.followupMission)
		End If
		Me.followupMission = Nothing
		Me.followupMissionProvider = Nothing
	End Sub

	' Token: 0x0600064F RID: 1615 RVA: 0x0004C1D5 File Offset: 0x0004A3D5
	Public Sub RegisterFollowupMission(targetMission As BaseMission, provider As IMissionProvider)
		Me.followupMission = targetMission
		Me.followupMissionProvider = provider
		If Me.followupMission IsNot Nothing AndAlso Me.followupMissionProvider IsNot Nothing Then
			MyBase.Invoke(AddressOf Me.AssignFollowUpMission, 1.5F)
		End If
	End Sub

	' Token: 0x170000BD RID: 189
	' (get) Token: 0x06000650 RID: 1616 RVA: 0x0004C212 File Offset: 0x0004A412
	Public ReadOnly Property HasPendingFollowupMission As Boolean
		Get
			Return MyBase.IsInvoking(AddressOf Me.AssignFollowUpMission)
		End Get
	End Property

	' Token: 0x06000651 RID: 1617 RVA: 0x0004C228 File Offset: 0x0004A428
	Private Function SaveMissions() As Missions
		Dim missions As Missions = Facepunch.Pool.[Get](Of Missions)()
		missions.missions = Facepunch.Pool.GetList(Of MissionInstance)()
		missions.activeMission = Me.GetActiveMission()
		missions.protocol = 253
		missions.seed = Global.World.Seed
		missions.saveCreatedTime = Epoch.FromDateTime(SaveRestore.SaveCreatedTime)
		For Each missionInstance As BaseMission.MissionInstance In Me.missions
			Dim missionInstance2 As MissionInstance = Facepunch.Pool.[Get](Of MissionInstance)()
			missionInstance2.missionID = missionInstance.missionID
			missionInstance2.missionStatus = CUInt(missionInstance.status)
			missions.missions.Add(missionInstance2)
			If missionInstance.status = BaseMission.MissionStatus.Active OrElse missionInstance.status = BaseMission.MissionStatus.Accomplished Then
				Dim missionInstanceData As MissionInstanceData = Facepunch.Pool.[Get](Of MissionInstanceData)()
				missionInstance2.instanceData = missionInstanceData
				missionInstanceData.providerID = missionInstance.providerID
				missionInstanceData.startTime = UnityEngine.Time.time - missionInstance.startTime
				missionInstanceData.endTime = missionInstance.endTime
				missionInstanceData.missionLocation = missionInstance.missionLocation
				missionInstanceData.missionPoints = Facepunch.Pool.GetList(Of ProtoBuf.MissionPoint)()
				For Each keyValuePair As KeyValuePair(Of String, Vector3) In missionInstance.missionPoints
					Dim missionPoint As ProtoBuf.MissionPoint = Facepunch.Pool.[Get](Of ProtoBuf.MissionPoint)()
					missionPoint.identifier = keyValuePair.Key
					missionPoint.location = keyValuePair.Value
					missionInstanceData.missionPoints.Add(missionPoint)
				Next
				missionInstanceData.objectiveStatuses = Facepunch.Pool.GetList(Of ObjectiveStatus)()
				For Each objectiveStatus As BaseMission.MissionInstance.ObjectiveStatus In missionInstance.objectiveStatuses
					Dim objectiveStatus2 As ObjectiveStatus = Facepunch.Pool.[Get](Of ObjectiveStatus)()
					objectiveStatus2.completed = objectiveStatus.completed
					objectiveStatus2.failed = objectiveStatus.failed
					objectiveStatus2.started = objectiveStatus.started
					objectiveStatus2.progressCurrent = objectiveStatus.progressCurrent
					objectiveStatus2.progressTarget = objectiveStatus.progressTarget
					missionInstanceData.objectiveStatuses.Add(objectiveStatus2)
				Next
				missionInstanceData.missionEntities = Facepunch.Pool.GetList(Of ProtoBuf.MissionEntity)()
				For Each keyValuePair2 As KeyValuePair(Of String, Global.MissionEntity) In missionInstance.missionEntities
					Dim baseEntity As Global.BaseEntity = If((keyValuePair2.Value IsNot Nothing), keyValuePair2.Value.GetEntity(), Nothing)
					If baseEntity.IsValid() Then
						Dim missionEntity As ProtoBuf.MissionEntity = Facepunch.Pool.[Get](Of ProtoBuf.MissionEntity)()
						missionEntity.identifier = keyValuePair2.Key
						missionEntity.entityID = baseEntity.net.ID
						missionInstanceData.missionEntities.Add(missionEntity)
					End If
				Next
			End If
		Next
		Return missions
	End Function

	' Token: 0x06000652 RID: 1618 RVA: 0x0004C518 File Offset: 0x0004A718
	Public Sub SetActiveMission(index As Integer)
		Dim activeMission As Integer = Me._activeMission
		Me._activeMission = index
		If Me.IsInTutorial AndAlso Me.GetCurrentTutorialIsland() IsNot Nothing Then
			Me.GetCurrentTutorialIsland().OnPlayerStartedMission(Me)
		End If
	End Sub

	' Token: 0x06000653 RID: 1619 RVA: 0x0004C54A File Offset: 0x0004A74A
	Public Function GetActiveMission() As Integer
		Return Me._activeMission
	End Function

	' Token: 0x06000654 RID: 1620 RVA: 0x0004C552 File Offset: 0x0004A752
	Public Function HasActiveMission() As Boolean
		Return Me.GetActiveMission() <> -1
	End Function

	' Token: 0x06000655 RID: 1621 RVA: 0x0004C560 File Offset: 0x0004A760
	Public Function GetActiveMissionInstance() As BaseMission.MissionInstance
		Dim activeMission As Integer = Me.GetActiveMission()
		If activeMission >= 0 AndAlso activeMission < Me.missions.Count Then
			Return Me.missions(activeMission)
		End If
		Return Nothing
	End Function

	' Token: 0x06000656 RID: 1622 RVA: 0x0004C594 File Offset: 0x0004A794
	Private Sub LoadMissions(loadedMissions As Missions)
		If Me.missions.Count > 0 Then
			For i As Integer = Me.missions.Count - 1 To 0 Step -1
				Dim missionInstance As BaseMission.MissionInstance = Me.missions(i)
				If missionInstance IsNot Nothing Then
					Facepunch.Pool.Free(Of BaseMission.MissionInstance)(missionInstance)
				End If
			Next
		End If
		Me.missions.Clear()
		If MyBase.isServer AndAlso loadedMissions IsNot Nothing Then
			Dim protocol As Integer = loadedMissions.protocol
			Dim seed As UInteger = loadedMissions.seed
			Dim saveCreatedTime As Integer = loadedMissions.saveCreatedTime
			Dim num As Integer = Epoch.FromDateTime(SaveRestore.SaveCreatedTime)
			If 253 <> protocol OrElse Global.World.Seed <> seed OrElse num <> saveCreatedTime Then
				Debug.Log("Missions were from old protocol or different seed, or not from a loaded save. Clearing")
				loadedMissions.activeMission = -1
				Me.SetActiveMission(-1)
				Me.State.missions = Me.SaveMissions()
				Return
			End If
		End If
		If loadedMissions IsNot Nothing AndAlso loadedMissions.missions.Count > 0 Then
			For Each missionInstance2 As MissionInstance In loadedMissions.missions
				If Not(MissionManifest.GetFromID(missionInstance2.missionID) Is Nothing) Then
					Dim missionInstance3 As BaseMission.MissionInstance = Facepunch.Pool.[Get](Of BaseMission.MissionInstance)()
					missionInstance3.missionID = missionInstance2.missionID
					missionInstance3.status = CType(missionInstance2.missionStatus, BaseMission.MissionStatus)
					Dim instanceData As MissionInstanceData = missionInstance2.instanceData
					If instanceData IsNot Nothing Then
						missionInstance3.providerID = instanceData.providerID
						missionInstance3.startTime = UnityEngine.Time.time - instanceData.startTime
						missionInstance3.endTime = instanceData.endTime
						missionInstance3.missionLocation = instanceData.missionLocation
						If MyBase.isServer AndAlso instanceData.missionPoints IsNot Nothing Then
							For Each missionPoint As ProtoBuf.MissionPoint In instanceData.missionPoints
								missionInstance3.missionPoints.Add(missionPoint.identifier, missionPoint.location)
								BaseMission.AddBlocker(missionPoint.location)
							Next
						End If
						missionInstance3.objectiveStatuses = New BaseMission.MissionInstance.ObjectiveStatus(instanceData.objectiveStatuses.Count - 1) {}
						For j As Integer = 0 To instanceData.objectiveStatuses.Count - 1
							Dim objectiveStatus As ObjectiveStatus = instanceData.objectiveStatuses(j)
							Dim objectiveStatus2 As BaseMission.MissionInstance.ObjectiveStatus = New BaseMission.MissionInstance.ObjectiveStatus()
							objectiveStatus2.completed = objectiveStatus.completed
							objectiveStatus2.failed = objectiveStatus.failed
							objectiveStatus2.started = objectiveStatus.started
							objectiveStatus2.progressCurrent = objectiveStatus.progressCurrent
							objectiveStatus2.progressTarget = objectiveStatus.progressTarget
							missionInstance3.objectiveStatuses(j) = objectiveStatus2
						Next
						If MyBase.isServer AndAlso instanceData.missionEntities IsNot Nothing Then
							missionInstance3.missionEntities.Clear()
							Dim mission As BaseMission = missionInstance3.GetMission()
							For Each missionEntity As ProtoBuf.MissionEntity In instanceData.missionEntities
								Dim missionEntity2 As Global.MissionEntity = Nothing
								Dim baseNetworkable As Global.BaseNetworkable = If((missionEntity.entityID <> Nothing), Global.BaseNetworkable.serverEntities.Find(missionEntity.entityID), Nothing)
								If baseNetworkable IsNot Nothing Then
									Dim missionEntity3 As Global.MissionEntity
									missionEntity2 = If(baseNetworkable.gameObject.TryGetComponent(Of Global.MissionEntity)(missionEntity3), missionEntity3, baseNetworkable.gameObject.AddComponent(Of Global.MissionEntity)())
									Dim missionEntityEntry As BaseMission.MissionEntityEntry
									If Not(mission IsNot Nothing) Then
										missionEntityEntry = Nothing
									Else
										Dim missionEntities As IReadOnlyCollection(Of BaseMission.MissionEntityEntry) = mission.missionEntities
										Dim <>9__186_ As Func(Of BaseMission.MissionEntityEntry, String) = Global.BasePlayer.<>c.<>9__186_0
										Dim selector As Func(Of BaseMission.MissionEntityEntry, String) = <>9__186_
										If <>9__186_ Is Nothing Then
											Dim func As Func(Of BaseMission.MissionEntityEntry, String) = Function(ed As BaseMission.MissionEntityEntry) ed.identifier
											selector = func
											Global.BasePlayer.<>c.<>9__186_0 = func
										End If
										missionEntityEntry = missionEntities.FindWith(selector, missionEntity.identifier, Nothing)
									End If
									Dim missionEntityEntry2 As BaseMission.MissionEntityEntry = missionEntityEntry
									missionEntity2.Setup(Me, missionInstance3, missionEntity.identifier, missionEntityEntry2 Is Nothing OrElse missionEntityEntry2.cleanupOnMissionSuccess, missionEntityEntry2 Is Nothing OrElse missionEntityEntry2.cleanupOnMissionFailed)
								End If
								missionInstance3.missionEntities.Add(missionEntity.identifier, missionEntity2)
							Next
						End If
					End If
					Me.missions.Add(missionInstance3)
				End If
			Next
			Me.SetActiveMission(loadedMissions.activeMission)
		Else
			Me.SetActiveMission(-1)
		End If
		If MyBase.isServer Then
			Dim activeMissionInstance As BaseMission.MissionInstance = Me.GetActiveMissionInstance()
			If activeMissionInstance IsNot Nothing Then
				activeMissionInstance.PostServerLoad(Me)
			End If
		End If
	End Sub

	' Token: 0x170000BE RID: 190
	' (get) Token: 0x06000657 RID: 1623 RVA: 0x0004CA04 File Offset: 0x0004AC04
	' (set) Token: 0x06000658 RID: 1624 RVA: 0x0004CA0C File Offset: 0x0004AC0C
	Public Property modelStateTick As ModelState

	' Token: 0x06000659 RID: 1625 RVA: 0x0004CA15 File Offset: 0x0004AC15
	Private Sub UpdateModelState()
		If Me.IsDead() Then
			Return
		End If
		If Me.IsSpectating() Then
			Return
		End If
		Me.wantsSendModelState = True
	End Sub

	' Token: 0x0600065A RID: 1626 RVA: 0x0004CA30 File Offset: 0x0004AC30
	Public Sub SendModelState(Optional force As Boolean = False)
		If Not force Then
			If Not Me.wantsSendModelState Then
				Return
			End If
			If Me.nextModelStateUpdate > UnityEngine.Time.time Then
				Return
			End If
		End If
		Me.wantsSendModelState = False
		Me.nextModelStateUpdate = UnityEngine.Time.time + 0.1F
		If Me.IsDead() Then
			Return
		End If
		If Me.IsSpectating() Then
			Return
		End If
		Me.modelState.sleeping = Me.IsSleeping()
		Me.modelState.mounted = Me.isMounted
		Me.modelState.relaxed = Me.IsRelaxed()
		Me.modelState.onPhone = (Me.HasActiveTelephone AndAlso Not Me.activeTelephone.IsMobile)
		Me.modelState.crawling = Me.IsCrawling()
		Me.modelState.loading = Me.IsLoadingAfterTransfer()
		MyBase.ClientRPC(Of ModelState)(RpcTarget.NetworkGroup("OnModelState"), Me.modelState)
	End Sub

	' Token: 0x170000BF RID: 191
	' (get) Token: 0x0600065B RID: 1627 RVA: 0x0004CB10 File Offset: 0x0004AD10
	Public ReadOnly Property isMounted As Boolean
		Get
			Return Me.mounted.IsValid(MyBase.isServer)
		End Get
	End Property

	' Token: 0x170000C0 RID: 192
	' (get) Token: 0x0600065C RID: 1628 RVA: 0x0004CB23 File Offset: 0x0004AD23
	Public ReadOnly Property isMountingHidingWeapon As Boolean
		Get
			Return Me.isMounted AndAlso Me.GetMounted().CanHoldItems()
		End Get
	End Property

	' Token: 0x0600065D RID: 1629 RVA: 0x0004CB3A File Offset: 0x0004AD3A
	Public Function GetMounted() As BaseMountable
		Return TryCast(Me.mounted.[Get](MyBase.isServer), BaseMountable)
	End Function

	' Token: 0x0600065E RID: 1630 RVA: 0x0004CB54 File Offset: 0x0004AD54
	Public Function GetMountedVehicle() As Global.BaseVehicle
		Dim baseMountable As BaseMountable = Me.GetMounted()
		If Not baseMountable.IsValid() Then
			Return Nothing
		End If
		Return baseMountable.VehicleParent()
	End Function

	' Token: 0x0600065F RID: 1631 RVA: 0x0004CB78 File Offset: 0x0004AD78
	Public Sub MarkSwapSeat()
		Me.nextSeatSwapTime = UnityEngine.Time.time + 0.75F
	End Sub

	' Token: 0x06000660 RID: 1632 RVA: 0x0004CB8B File Offset: 0x0004AD8B
	Public Function SwapSeatCooldown() As Boolean
		Return UnityEngine.Time.time < Me.nextSeatSwapTime
	End Function

	' Token: 0x06000661 RID: 1633 RVA: 0x0004CB9A File Offset: 0x0004AD9A
	Public Function CanMountMountablesNow() As Boolean
		Return Not Me.IsDead() AndAlso Not Me.IsWounded()
	End Function

	' Token: 0x06000662 RID: 1634 RVA: 0x0004CBAF File Offset: 0x0004ADAF
	Public Sub MountObject(mount As BaseMountable, Optional desiredSeat As Integer = 0)
		Me.mounted.[Set](mount)
		MyBase.SendNetworkUpdate(Global.BasePlayer.NetworkQueue.Update)
	End Sub

	' Token: 0x06000663 RID: 1635 RVA: 0x0004CBC4 File Offset: 0x0004ADC4
	Public Sub EnsureDismounted()
		If Me.isMounted Then
			Me.GetMounted().DismountPlayer(Me, False)
		End If
	End Sub

	' Token: 0x06000664 RID: 1636 RVA: 0x0004CBDB File Offset: 0x0004ADDB
	Public Overridable Sub DismountObject()
		Me.mounted.[Set](Nothing)
		MyBase.SendNetworkUpdate(Global.BasePlayer.NetworkQueue.Update)
		Me.PauseSpeedHackDetection(5F)
		Me.PauseVehicleNoClipDetection(5F)
	End Sub

	' Token: 0x06000665 RID: 1637 RVA: 0x0004CC08 File Offset: 0x0004AE08
	Public Sub HandleMountedOnLoad()
		If Me.mounted.IsValid(MyBase.isServer) Then
			Dim baseMountable As BaseMountable = TryCast(Me.mounted.[Get](MyBase.isServer), BaseMountable)
			If baseMountable IsNot Nothing Then
				baseMountable.MountPlayer(Me)
				If Not Me.AllowSleeperMounting(baseMountable) Then
					baseMountable.DismountPlayer(Me, False)
					Return
				End If
			Else
				Me.mounted.[Set](Nothing)
			End If
		End If
	End Sub

	' Token: 0x06000666 RID: 1638 RVA: 0x0004CC6D File Offset: 0x0004AE6D
	Public Function AllowSleeperMounting(mountable As BaseMountable) As Boolean
		Return mountable.allowSleeperMounting OrElse Me.IsLoadingAfterTransfer() OrElse MyBase.IsTransferProtected()
	End Function

	' Token: 0x06000667 RID: 1639 RVA: 0x0004CC8C File Offset: 0x0004AE8C
	Public Function SaveSecondaryData() As PlayerSecondaryData
		Dim playerSecondaryData As PlayerSecondaryData = Facepunch.Pool.[Get](Of PlayerSecondaryData)()
		playerSecondaryData.userId = Me.userID
		Dim playerState As PlayerState = Me.State.Copy()
		If playerState.pointsOfInterest IsNot Nothing Then
			Facepunch.Pool.FreeListAndItems(Of MapNote)(playerState.pointsOfInterest)
		End If
		If playerState.pings IsNot Nothing Then
			Facepunch.Pool.FreeListAndItems(Of MapNote)(playerState.pings)
		End If
		Dim deathMarker As MapNote = playerState.deathMarker
		If deathMarker IsNot Nothing Then
			deathMarker.Dispose()
		End If
		playerState.deathMarker = Nothing
		Dim missions As Missions = playerState.missions
		If missions IsNot Nothing Then
			missions.Dispose()
		End If
		playerState.missions = Nothing
		playerSecondaryData.playerState = playerState
		If Me.currentTeam <> 0UL Then
			Dim playerTeam As Global.RelationshipManager.PlayerTeam = Global.RelationshipManager.ServerInstance.FindTeam(Me.currentTeam)
			If playerTeam IsNot Nothing Then
				playerSecondaryData.teamId = playerTeam.teamID
				playerSecondaryData.isTeamLeader = (playerTeam.teamLeader = Me.userID)
			End If
		End If
		playerSecondaryData.relationships = Facepunch.Pool.GetList(Of PlayerSecondaryData.RelationshipData)()
		For Each playerRelationshipInfo As Global.RelationshipManager.PlayerRelationshipInfo In Global.RelationshipManager.ServerInstance.GetRelationships(Me.userID).relations.Values
			Dim relationshipData As PlayerSecondaryData.RelationshipData = Facepunch.Pool.[Get](Of PlayerSecondaryData.RelationshipData)()
			relationshipData.info = playerRelationshipInfo.ToProto()
			relationshipData.mugshotData = Me.<SaveSecondaryData>g__GetPoolableMugshotData|212_0(playerRelationshipInfo)
			playerSecondaryData.relationships.Add(relationshipData)
		Next
		Return playerSecondaryData
	End Function

	' Token: 0x06000668 RID: 1640 RVA: 0x0004CDF0 File Offset: 0x0004AFF0
	Public Sub LoadSecondaryData(data As PlayerSecondaryData)
		If data Is Nothing Then
			Return
		End If
		If data.userId <> Me.userID Then
			Debug.LogError(String.Format("Attempted to load secondary data with an incorrect userID! Expected {0} but player has {1}, not loading it.", data.userId, Me.userID))
			Return
		End If
		If data.playerState IsNot Nothing Then
			Me.State.unHostileTimestamp = data.playerState.unHostileTimestamp
			Me.DirtyPlayerState()
		End If
		If data.relationships IsNot Nothing Then
			Dim relationships As Global.RelationshipManager.PlayerRelationships = Global.RelationshipManager.ServerInstance.GetRelationships(Me.userID)
			relationships.relations.Clear()
			For Each relationshipData As PlayerSecondaryData.RelationshipData In data.relationships
				If relationshipData.mugshotData.Count > 0 Then
					Try
						Dim array As Byte() = New Byte(relationshipData.mugshotData.Count - 1) {}
						relationshipData.mugshotData.AsSpan().CopyTo(array)
						Dim steamIdHash As UInteger = Global.RelationshipManager.GetSteamIdHash(Me.userID, relationshipData.info.playerID)
						Dim num As UInteger = FileStorage.server.Store(array, FileStorage.Type.jpg, Global.RelationshipManager.ServerInstance.net.ID, steamIdHash)
						If num <> relationshipData.info.mugshotCrc Then
							Debug.LogWarning(String.Format("Mugshot data for {0}->{1} had a CRC mismatch, updating it", Me.userID, relationshipData.info.playerID))
							relationshipData.info.mugshotCrc = num
						End If
					Catch exception As Exception
						Debug.LogException(exception)
					End Try
				End If
				relationships.relations.Add(relationshipData.info.playerID, Global.RelationshipManager.PlayerRelationshipInfo.FromProto(relationshipData.info))
			Next
			Global.RelationshipManager.ServerInstance.MarkRelationshipsDirtyFor(Me)
		End If
	End Sub

	' Token: 0x06000669 RID: 1641 RVA: 0x0004CFE8 File Offset: 0x0004B1E8
	Public Overrides Sub DisableTransferProtection()
		Dim vehicleParent As Global.BaseVehicle = Me.GetVehicleParent()
		If vehicleParent IsNot Nothing AndAlso vehicleParent.IsTransferProtected() Then
			vehicleParent.DisableTransferProtection()
		End If
		Dim baseMountable As BaseMountable = Me.GetMounted()
		If baseMountable IsNot Nothing AndAlso baseMountable.IsTransferProtected() Then
			baseMountable.DisableTransferProtection()
		End If
		MyBase.DisableTransferProtection()
	End Sub

	' Token: 0x0600066A RID: 1642 RVA: 0x0004D037 File Offset: 0x0004B237
	Public Sub KickAfterServerTransfer()
		If Me.IsConnected Then
			Me.Kick("Redirecting to another zone...")
		End If
		MyBase.Kill(Global.BaseNetworkable.DestroyMode.None)
	End Sub

	' Token: 0x0600066B RID: 1643 RVA: 0x0004D053 File Offset: 0x0004B253
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.FromOwner()>
	<Global.BaseEntity.RPC_Server.CallsPerSecond(5UL)>
	Private Sub RequestParachuteDeploy(msg As Global.BaseEntity.RPCMessage)
		Me.RequestParachuteDeploy()
	End Sub

	' Token: 0x0600066C RID: 1644 RVA: 0x0004D05C File Offset: 0x0004B25C
	Public Sub RequestParachuteDeploy()
		If Me.isMounted OrElse Not Me.CheckParachuteClearance() Then
			Return
		End If
		Dim slot As Global.Item = Me.inventory.containerWear.GetSlot(7)
		Dim itemModParachute As ItemModParachute
		If slot IsNot Nothing AndAlso slot.conditionNormalized > 0F AndAlso Not slot.isBroken AndAlso slot.info.TryGetComponent(Of ItemModParachute)(itemModParachute) Then
			Dim parachute As Parachute = TryCast(GameManager.server.CreateEntity(itemModParachute.ParachuteVehiclePrefab.resourcePath, MyBase.transform.position, Me.eyes.rotation, True), Parachute)
			If parachute IsNot Nothing Then
				parachute.skinID = slot.skin
				parachute.Spawn()
				parachute.SetHealth(parachute.MaxHealth() * slot.conditionNormalized)
				parachute.AttemptMount(Me, True)
				If Me.isMounted Then
					slot.Remove(0F)
					ItemManager.DoRemoves()
					MyBase.SendNetworkUpdate(Global.BasePlayer.NetworkQueue.Update)
					Return
				End If
				parachute.Kill(Global.BaseNetworkable.DestroyMode.None)
			End If
		End If
	End Sub

	' Token: 0x0600066D RID: 1645 RVA: 0x0004D150 File Offset: 0x0004B350
	Public Function CheckParachuteClearance() As Boolean
		Dim position As Vector3 = MyBase.transform.position
		Dim raycastHit As RaycastHit
		Return Not WaterLevel.Test(position - Vector3.up * 5F, False, True, Me) AndAlso Not GamePhysics.Trace(New Ray(position, -Vector3.up), 1F, raycastHit, 6F, 1218543873, QueryTriggerInteraction.UseGlobal, Nothing) AndAlso Not GamePhysics.CheckSphere(position + Vector3.up * 3.5F, 2F, 1218543873, QueryTriggerInteraction.UseGlobal)
	End Function

	' Token: 0x0600066E RID: 1646 RVA: 0x0004D1DC File Offset: 0x0004B3DC
	Public Function HasValidParachuteEquipped() As Boolean
		If Me.inventory Is Nothing OrElse Me.inventory.containerWear Is Nothing Then
			Return False
		End If
		Dim slot As Global.Item = Me.inventory.containerWear.GetSlot(7)
		Dim itemModParachute As ItemModParachute
		Return slot IsNot Nothing AndAlso slot.conditionNormalized > 0F AndAlso Not slot.isBroken AndAlso slot.info.TryGetComponent(Of ItemModParachute)(itemModParachute)
	End Function

	' Token: 0x0600066F RID: 1647 RVA: 0x0004D242 File Offset: 0x0004B442
	Public Sub ClearClientPetLink()
		MyBase.ClientRPC(Of Integer, Integer)(RpcTarget.Player("CLIENT_SetPetPrefabID", Me), 0, 0)
	End Sub

	' Token: 0x06000670 RID: 1648 RVA: 0x0004D258 File Offset: 0x0004B458
	Public Sub SendClientPetLink()
		Dim basePet As BasePet
		If Me.PetEntity Is Nothing AndAlso BasePet.ActivePetByOwnerID.TryGetValue(Me.userID, basePet) AndAlso basePet.Brain IsNot Nothing Then
			basePet.Brain.SetOwningPlayer(Me)
		End If
		MyBase.ClientRPC(Of UInteger, NetworkableId)(RpcTarget.Player("CLIENT_SetPetPrefabID", Me), If((Me.PetEntity IsNot Nothing), Me.PetEntity.prefabID, 0UI), If((Me.PetEntity IsNot Nothing), Me.PetEntity.net.ID, Nothing))
		If Me.PetEntity IsNot Nothing Then
			Me.SendClientPetStateIndex()
		End If
	End Sub

	' Token: 0x06000671 RID: 1649 RVA: 0x0004D310 File Offset: 0x0004B510
	Public Sub SendClientPetStateIndex()
		Dim basePet As BasePet = TryCast(Me.PetEntity, BasePet)
		If basePet Is Nothing Then
			Return
		End If
		MyBase.ClientRPC(Of Integer)(RpcTarget.Player("CLIENT_SetPetPetLoadedStateIndex", Me), basePet.Brain.LoadedDesignIndex())
	End Sub

	' Token: 0x06000672 RID: 1650 RVA: 0x0004D34F File Offset: 0x0004B54F
	<Global.BaseEntity.RPC_Server()>
	Private Sub IssuePetCommand(msg As Global.BaseEntity.RPCMessage)
		Me.ParsePetCommand(msg, False)
	End Sub

	' Token: 0x06000673 RID: 1651 RVA: 0x0004D359 File Offset: 0x0004B559
	<Global.BaseEntity.RPC_Server()>
	Private Sub IssuePetCommandRaycast(msg As Global.BaseEntity.RPCMessage)
		Me.ParsePetCommand(msg, True)
	End Sub

	' Token: 0x06000674 RID: 1652 RVA: 0x0004D364 File Offset: 0x0004B564
	Private Sub ParsePetCommand(msg As Global.BaseEntity.RPCMessage, raycast As Boolean)
		If UnityEngine.Time.time - Me.lastPetCommandIssuedTime <= 1F Then
			Return
		End If
		Me.lastPetCommandIssuedTime = UnityEngine.Time.time
		If msg.player Is Nothing Then
			Return
		End If
		If Me.Pet Is Nothing Then
			Return
		End If
		If Not Me.Pet.IsOwnedBy(msg.player) Then
			Return
		End If
		Dim cmd As Integer = msg.read.Int32()
		Dim param As Integer = msg.read.Int32()
		If raycast Then
			Dim value As Ray = msg.read.Ray()
			Me.Pet.IssuePetCommand(CType(cmd, PetCommandType), param, New Ray?(value))
			Return
		End If
		Me.Pet.IssuePetCommand(CType(cmd, PetCommandType), param, Nothing)
	End Sub

	' Token: 0x06000675 RID: 1653 RVA: 0x0004D410 File Offset: 0x0004B610
	Public Function CanPing(Optional disregardHeldEntity As Boolean = False) As Boolean
		Dim activeGameMode As BaseGameMode = BaseGameMode.GetActiveGameMode(MyBase.isServer)
		If activeGameMode IsNot Nothing AndAlso Not activeGameMode.allowPings Then
			Return False
		End If
		Dim flag As Boolean
		If Not disregardHeldEntity AndAlso Not(TypeOf Me.GetHeldEntity()Is Binocular) Then
			If Me.isMounted Then
				Dim computerStation As Global.ComputerStation = TryCast(Me.GetMounted(), Global.ComputerStation)
				If computerStation IsNot Nothing Then
					flag = computerStation.AllowPings()
					GoTo IL_52
				End If
			End If
			flag = False
		Else
			flag = True
		End If
		IL_52:
		Return flag AndAlso Me.IsAlive() AndAlso Not Me.IsWounded() AndAlso Not Me.IsSpectating()
	End Function

	' Token: 0x06000676 RID: 1654 RVA: 0x0004D48C File Offset: 0x0004B68C
	Public Shared Function GetPingStyle(t As Global.BasePlayer.PingType) As Global.BasePlayer.PingStyle
		Dim result As Global.BasePlayer.PingStyle = Nothing
		Select Case t
			Case Global.BasePlayer.PingType.Hostile
				result = Global.BasePlayer.HostileMarker
			Case Global.BasePlayer.PingType.[GoTo]
				result = Global.BasePlayer.GoToMarker
			Case Global.BasePlayer.PingType.Dollar
				result = Global.BasePlayer.DollarMarker
			Case Global.BasePlayer.PingType.Loot
				result = Global.BasePlayer.LootMarker
			Case Global.BasePlayer.PingType.Node
				result = Global.BasePlayer.NodeMarker
			Case Global.BasePlayer.PingType.Gun
				result = Global.BasePlayer.GunMarker
			Case Global.BasePlayer.PingType.Build
				result = Global.BasePlayer.BuildMarker
		End Select
		Return result
	End Function

	' Token: 0x06000677 RID: 1655 RVA: 0x0004D4FC File Offset: 0x0004B6FC
	Private Sub ApplyPingStyle(note As MapNote, type As Global.BasePlayer.PingType)
		Dim pingStyle As Global.BasePlayer.PingStyle = Global.BasePlayer.GetPingStyle(type)
		note.colourIndex = pingStyle.ColourIndex
		note.icon = pingStyle.IconIndex
	End Sub

	' Token: 0x06000678 RID: 1656 RVA: 0x0004D528 File Offset: 0x0004B728
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.FromOwner()>
	<Global.BaseEntity.RPC_Server.CallsPerSecond(3UL)>
	Private Sub Server_AddPing(msg As Global.BaseEntity.RPCMessage)
		If Me.State.pings Is Nothing Then
			Me.State.pings = New List(Of MapNote)()
		End If
		If ConVar.Server.maximumPings = 0 OrElse Not Me.CanPing(False) Then
			Return
		End If
		Dim vector As Vector3 = msg.read.Vector3()
		Dim pingType As Global.BasePlayer.PingType = CType(Mathf.Clamp(msg.read.Int32(), 0, 6), Global.BasePlayer.PingType)
		Dim wasViaWheel As Boolean = msg.read.Bit()
		Dim pingStyle As Global.BasePlayer.PingStyle = Global.BasePlayer.GetPingStyle(pingType)
		For Each mapNote As MapNote In Me.State.pings
			If mapNote.icon = pingStyle.IconIndex AndAlso (mapNote.worldPosition - vector).sqrMagnitude < 0.75F Then
				Return
			End If
		Next
		If Me.State.pings.Count >= ConVar.Server.maximumPings Then
			Me.State.pings.RemoveAt(0)
		End If
		Dim mapNote2 As MapNote = Facepunch.Pool.[Get](Of MapNote)()
		mapNote2.worldPosition = vector
		mapNote2.isPing = True
		Dim mapNote3 As MapNote = mapNote2
		Dim mapNote4 As MapNote = mapNote2
		Dim pingDuration As Single = ConVar.Server.pingDuration
		Dim timeRemaining As Single = pingDuration
		mapNote4.totalDuration = pingDuration
		mapNote3.timeRemaining = timeRemaining
		Me.ApplyPingStyle(mapNote2, pingType)
		Me.State.pings.Add(mapNote2)
		Me.DirtyPlayerState()
		Me.SendPingsToClient()
		Me.TeamUpdate(True)
		Analytics.Azure.OnPlayerPinged(Me, pingType, wasViaWheel)
	End Sub

	' Token: 0x06000679 RID: 1657 RVA: 0x0004D69C File Offset: 0x0004B89C
	Public Sub AddPingAtLocation(type As Global.BasePlayer.PingType, location As Vector3, time As Single, associatedId As NetworkableId)
		If Me.State.pings IsNot Nothing Then
			Dim pingStyle As Global.BasePlayer.PingStyle = Global.BasePlayer.GetPingStyle(type)
			For Each mapNote As MapNote In Me.State.pings
				If mapNote.icon = pingStyle.IconIndex AndAlso Vector3.Distance(location, mapNote.worldPosition) < 0.25F Then
					Return
				End If
			Next
		End If
		If Me.State.pings Is Nothing Then
			Me.State.pings = New List(Of MapNote)()
		End If
		Dim mapNote2 As MapNote = Facepunch.Pool.[Get](Of MapNote)()
		mapNote2.worldPosition = location
		mapNote2.isPing = True
		Dim mapNote3 As MapNote = mapNote2
		mapNote2.totalDuration = time
		mapNote3.timeRemaining = time
		mapNote2.associatedId = associatedId
		Me.ApplyPingStyle(mapNote2, type)
		Me.State.pings.Add(mapNote2)
		Me.DirtyPlayerState()
		Me.SendPingsToClient()
		Me.TeamUpdate(False)
	End Sub

	' Token: 0x0600067A RID: 1658 RVA: 0x0004D7A0 File Offset: 0x0004B9A0
	Public Sub RemovePingAtLocation(type As Global.BasePlayer.PingType, location As Vector3, tolerance As Single, associatedId As NetworkableId)
		If Me.State.pings IsNot Nothing Then
			Dim pingStyle As Global.BasePlayer.PingStyle = Global.BasePlayer.GetPingStyle(type)
			For i As Integer = 0 To Me.State.pings.Count - 1
				Dim mapNote As MapNote = Me.State.pings(i)
				If mapNote.icon = pingStyle.IconIndex AndAlso Vector3.Distance(location, mapNote.worldPosition) < tolerance Then
					Me.State.pings.RemoveAt(i)
					Me.DirtyPlayerState()
					Me.SendPingsToClient()
					Me.TeamUpdate(False)
				End If
			Next
		End If
	End Sub

	' Token: 0x0600067B RID: 1659 RVA: 0x0004D830 File Offset: 0x0004BA30
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.FromOwner()>
	<Global.BaseEntity.RPC_Server.CallsPerSecond(3UL)>
	Private Sub Server_RemovePing(msg As Global.BaseEntity.RPCMessage)
		If Me.State.pings Is Nothing Then
			Me.State.pings = New List(Of MapNote)()
		End If
		Dim num As Integer = msg.read.Int32()
		If num >= 0 AndAlso num < Me.State.pings.Count Then
			Me.State.pings.RemoveAt(num)
			Me.DirtyPlayerState()
			Me.SendPingsToClient()
			Me.TeamUpdate(True)
		End If
	End Sub

	' Token: 0x0600067C RID: 1660 RVA: 0x0004D8A4 File Offset: 0x0004BAA4
	Private Sub SendPingsToClient()
		Using mapNoteList As MapNoteList = Facepunch.Pool.[Get](Of MapNoteList)()
			mapNoteList.notes = Facepunch.Pool.GetList(Of MapNote)()
			mapNoteList.notes.AddRange(Me.State.pings)
			MyBase.ClientRPC(Of MapNoteList)(RpcTarget.Player("Client_ReceivePings", Me), mapNoteList)
			mapNoteList.notes.Clear()
		End Using
	End Sub

	' Token: 0x170000C1 RID: 193
	' (get) Token: 0x0600067D RID: 1661 RVA: 0x0004D914 File Offset: 0x0004BB14
	Private ReadOnly Property TotalPingCount As Integer
		Get
			If Me.State.pings Is Nothing Then
				Return 0
			End If
			Return Me.State.pings.Count
		End Get
	End Property

	' Token: 0x0600067E RID: 1662 RVA: 0x0004D938 File Offset: 0x0004BB38
	Private Sub TickPings()
		If Me.lastTick < 0.5F Then
			Return
		End If
		Dim ts As TimeSince = Me.lastTick
		Me.lastTick = 0F
		Me.UpdateResourcePings()
		If Me.State.pings Is Nothing Then
			Return
		End If
		Dim list As List(Of MapNote) = Facepunch.Pool.GetList(Of MapNote)()
		For Each mapNote As MapNote In Me.State.pings
			mapNote.timeRemaining -= ts
			If mapNote.timeRemaining <= 0F Then
				list.Add(mapNote)
			End If
		Next
		Dim count As Integer = list.Count
		For Each item As MapNote In list
			If Me.State.pings.Contains(item) Then
				Me.State.pings.Remove(item)
			End If
		Next
		Facepunch.Pool.FreeList(Of MapNote)(list)
		If count > 0 Then
			Me.DirtyPlayerState()
			Me.SendPingsToClient()
			Me.TeamUpdate(True)
		End If
	End Sub

	' Token: 0x0600067F RID: 1663 RVA: 0x0004DA7C File Offset: 0x0004BC7C
	Public Sub RegisterPingedEntity(entity As Global.BaseEntity, type As Global.BasePlayer.PingType)
		If Not Me.pingedEntities.Contains(New ValueTuple(Of NetworkableId, Global.BasePlayer.PingType)(entity.net.ID, type)) Then
			Me.pingedEntities.Add(New ValueTuple(Of NetworkableId, Global.BasePlayer.PingType)(entity.net.ID, type))
		End If
	End Sub

	' Token: 0x06000680 RID: 1664 RVA: 0x0004DAB8 File Offset: 0x0004BCB8
	Public Sub DeregisterPingedEntitiesOfType(type As Global.BasePlayer.PingType)
		Dim list As List(Of ValueTuple(Of NetworkableId, Global.BasePlayer.PingType)) = Facepunch.Pool.GetList(Of ValueTuple(Of NetworkableId, Global.BasePlayer.PingType))()
		For Each valueTuple As ValueTuple(Of NetworkableId, Global.BasePlayer.PingType) In Me.pingedEntities
			If valueTuple.Item2 = type Then
				list.Add(valueTuple)
			End If
		Next
		For Each item As ValueTuple(Of NetworkableId, Global.BasePlayer.PingType) In list
			Me.pingedEntities.Remove(item)
		Next
		Facepunch.Pool.FreeList(Of ValueTuple(Of NetworkableId, Global.BasePlayer.PingType))(list)
	End Sub

	' Token: 0x06000681 RID: 1665 RVA: 0x0004DB68 File Offset: 0x0004BD68
	Public Sub DeregisterPingedEntity(id As NetworkableId, type As Global.BasePlayer.PingType)
		If Me.pingedEntities.Contains(New ValueTuple(Of NetworkableId, Global.BasePlayer.PingType)(id, type)) Then
			Me.pingedEntities.Remove(New ValueTuple(Of NetworkableId, Global.BasePlayer.PingType)(id, type))
			For i As Integer = 0 To Me.State.pings.Count - 1
				If Me.State.pings(i).associatedId = id Then
					Me.State.pings.RemoveAt(i)
					Exit For
				End If
			Next
			Me.DirtyPlayerState()
			Me.SendPingsToClient()
		End If
	End Sub

	' Token: 0x06000682 RID: 1666 RVA: 0x0004DBF4 File Offset: 0x0004BDF4
	Public Sub EnableResourcePings(forItem As ItemDefinition, pingType As Global.BasePlayer.PingType)
		If Not Me.tutorialDesiredResource.Contains(New ValueTuple(Of ItemDefinition, Global.BasePlayer.PingType)(forItem, pingType)) Then
			Me.tutorialDesiredResource.Add(New ValueTuple(Of ItemDefinition, Global.BasePlayer.PingType)(forItem, pingType))
		End If
	End Sub

	' Token: 0x06000683 RID: 1667 RVA: 0x0004DC1C File Offset: 0x0004BE1C
	Private Sub UpdateResourcePings()
		If Me.State Is Nothing Then
			Return
		End If
		If Me.lastResourcePingUpdate < 3F Then
			Return
		End If
		If Not Me.IsInTutorial Then
			Return
		End If
		Me.lastResourcePingUpdate = 0F
		If Me.State.pings Is Nothing Then
			Me.State.pings = New List(Of MapNote)()
		End If
		Dim list As List(Of Global.BaseEntity) = Facepunch.Pool.GetList(Of Global.BaseEntity)()
		Dim list2 As List(Of ValueTuple(Of Global.BaseEntity, Global.BasePlayer.PingType)) = Facepunch.Pool.GetList(Of ValueTuple(Of Global.BaseEntity, Global.BasePlayer.PingType))()
		Dim list3 As List(Of Global.BaseEntity) = Facepunch.Pool.GetList(Of Global.BaseEntity)()
		For Each valueTuple As ValueTuple(Of ItemDefinition, Global.BasePlayer.PingType) In Me.tutorialDesiredResource
			list3.Clear()
			For Each networkable As Networkable In Me.net.group.networkables
				Dim baseEntity As Global.BaseEntity = TryCast(Global.BaseNetworkable.serverEntities.Find(networkable.ID), Global.BaseEntity)
				If baseEntity IsNot Nothing AndAlso MyBase.Distance(baseEntity) < 128F AndAlso baseEntity.isServer Then
					Dim resourceDispenser As ResourceDispenser
					If baseEntity.TryGetComponent(Of ResourceDispenser)(resourceDispenser) AndAlso resourceDispenser.HasItemToDispense(valueTuple.Item1) Then
						list3.Add(baseEntity)
					Else
						Dim collectibleEntity As CollectibleEntity = TryCast(baseEntity, CollectibleEntity)
						If collectibleEntity IsNot Nothing AndAlso collectibleEntity.HasItem(valueTuple.Item1) Then
							list3.Add(baseEntity)
						Else
							Dim storageContainer As StorageContainer = TryCast(baseEntity, StorageContainer)
							If storageContainer IsNot Nothing AndAlso storageContainer.inventory IsNot Nothing AndAlso storageContainer.inventory.HasItem(valueTuple.Item1) Then
								list3.Add(baseEntity)
							End If
						End If
					End If
				End If
			Next
			If list3.Count > 0 Then
				Dim num As Single = Single.MaxValue
				Dim baseEntity2 As Global.BaseEntity = Nothing
				For Each baseEntity3 As Global.BaseEntity In list3
					Dim num2 As Single = MyBase.Distance(baseEntity3)
					If num2 < num Then
						num = num2
						baseEntity2 = baseEntity3
					End If
				Next
				If baseEntity2 IsNot Nothing Then
					list2.Add(New ValueTuple(Of Global.BaseEntity, Global.BasePlayer.PingType)(baseEntity2, valueTuple.Item2))
				End If
			End If
		Next
		Dim list4 As List(Of ValueTuple(Of NetworkableId, Global.BasePlayer.PingType)) = Facepunch.Pool.GetList(Of ValueTuple(Of NetworkableId, Global.BasePlayer.PingType))()
		For Each valueTuple2 As ValueTuple(Of NetworkableId, Global.BasePlayer.PingType) In Me.pingedEntities
			Dim baseNetworkable As Global.BaseNetworkable = Global.BaseNetworkable.serverEntities.Find(valueTuple2.Item1)
			If baseNetworkable IsNot Nothing AndAlso Not baseNetworkable.IsDestroyed Then
				list2.Add(New ValueTuple(Of Global.BaseEntity, Global.BasePlayer.PingType)(TryCast(baseNetworkable, Global.BaseEntity), valueTuple2.Item2))
			Else
				list4.Add(valueTuple2)
			End If
		Next
		For Each item As ValueTuple(Of NetworkableId, Global.BasePlayer.PingType) In list4
			Me.pingedEntities.Remove(item)
		Next
		Facepunch.Pool.FreeList(Of ValueTuple(Of NetworkableId, Global.BasePlayer.PingType))(list4)
		Facepunch.Pool.FreeList(Of Global.BaseEntity)(list3)
		Dim list5 As List(Of MapNote) = Facepunch.Pool.GetList(Of MapNote)()
		For Each mapNote As MapNote In Me.State.pings
			If mapNote.associatedId.Value <> 0UL Then
				Dim flag As Boolean = False
				For Each valueTuple3 As ValueTuple(Of Global.BaseEntity, Global.BasePlayer.PingType) In list2
					If mapNote.associatedId = valueTuple3.Item1.net.ID Then
						flag = True
						Exit For
					End If
				Next
				If Not flag Then
					Dim baseNetworkable2 As Global.BaseNetworkable = Global.BaseNetworkable.serverEntities.Find(mapNote.associatedId)
					If baseNetworkable2 IsNot Nothing Then
						Dim entityPingSource As IEntityPingSource = TryCast(baseNetworkable2, IEntityPingSource)
						If entityPingSource IsNot Nothing AndAlso entityPingSource.IsPingValid(mapNote) Then
							flag = True
						End If
					End If
				End If
				If Not flag Then
					list5.Add(mapNote)
				End If
			End If
		Next
		Dim flag2 As Boolean = list5.Count > 0
		For Each item2 As MapNote In list5
			If Me.State.pings.Contains(item2) Then
				Me.State.pings.Remove(item2)
			End If
		Next
		Facepunch.Pool.FreeList(Of MapNote)(list5)
		For Each valueTuple4 As ValueTuple(Of Global.BaseEntity, Global.BasePlayer.PingType) In list2
			If Not Me.HasPingForEntity(valueTuple4.Item1) Then
				Dim item3 As Global.BasePlayer.PingType = valueTuple4.Item2
				For Each valueTuple5 As ValueTuple(Of NetworkableId, Global.BasePlayer.PingType) In Me.pingedEntities
					If valueTuple5.Item1 = valueTuple4.Item1.net.ID Then
						item3 = valueTuple5.Item2
					End If
				Next
				Me.State.pings.Add(Me.CreatePingForEntity(valueTuple4.Item1, item3))
				flag2 = True
			End If
		Next
		If flag2 Then
			Me.DirtyPlayerState()
			Me.SendPingsToClient()
		End If
		Facepunch.Pool.FreeList(Of Global.BaseEntity)(list)
	End Sub

	' Token: 0x06000684 RID: 1668 RVA: 0x0004E234 File Offset: 0x0004C434
	Private Function CreatePingForEntity(baseEntity As Global.BaseEntity, type As Global.BasePlayer.PingType) As MapNote
		Dim mapNote As MapNote = Facepunch.Pool.[Get](Of MapNote)()
		mapNote.worldPosition = baseEntity.transform.position
		mapNote.isPing = True
		Dim mapNote2 As MapNote = mapNote
		Dim mapNote3 As MapNote = mapNote
		Dim num As Single = 30F
		Dim timeRemaining As Single = num
		mapNote3.totalDuration = num
		mapNote2.timeRemaining = timeRemaining
		mapNote.associatedId = baseEntity.net.ID
		Me.ApplyPingStyle(mapNote, type)
		Return mapNote
	End Function

	' Token: 0x06000685 RID: 1669 RVA: 0x0004E28D File Offset: 0x0004C48D
	Private Function HasPingForEntity(ent As Global.BaseEntity) As Boolean
		Return Me.HasPingForEntity(ent.net.ID)
	End Function

	' Token: 0x06000686 RID: 1670 RVA: 0x0004E2A0 File Offset: 0x0004C4A0
	Private Function HasPingForEntity(id As NetworkableId) As Boolean
		Using enumerator As List(Of MapNote).Enumerator = Me.State.pings.GetEnumerator()
			While enumerator.MoveNext()
				If enumerator.Current.associatedId = id Then
					Return True
				End If
			End While
		End Using
		Return False
	End Function

	' Token: 0x06000687 RID: 1671 RVA: 0x0004E304 File Offset: 0x0004C504
	Public Sub DisableResourcePings(forItem As ItemDefinition, type As Global.BasePlayer.PingType)
		If Me.tutorialDesiredResource.Contains(New ValueTuple(Of ItemDefinition, Global.BasePlayer.PingType)(forItem, type)) Then
			Me.tutorialDesiredResource.Remove(New ValueTuple(Of ItemDefinition, Global.BasePlayer.PingType)(forItem, type))
		End If
		If Me.tutorialDesiredResource.Count = 0 Then
			Me.UpdateResourcePings()
		End If
	End Sub

	' Token: 0x06000688 RID: 1672 RVA: 0x0004E340 File Offset: 0x0004C540
	Private Sub ClearAllPings()
		If Me.State IsNot Nothing AndAlso Me.State.pings IsNot Nothing Then
			Me.State.pings.Clear()
		End If
		Me.tutorialDesiredResource.Clear()
		Me.pingedEntities.Clear()
	End Sub

	' Token: 0x170000C2 RID: 194
	' (get) Token: 0x06000689 RID: 1673 RVA: 0x0004E37D File Offset: 0x0004C57D
	Public ReadOnly Property State As PlayerState
		Get
			If Me.userID = 0UL Then
				Throw New InvalidOperationException("Cannot get player state without a SteamID")
			End If
			Return SingletonComponent(Of ServerMgr).Instance.playerStateManager.[Get](Me.userID)
		End Get
	End Property

	' Token: 0x170000C3 RID: 195
	' (get) Token: 0x0600068A RID: 1674 RVA: 0x0004E3B1 File Offset: 0x0004C5B1
	Public ReadOnly Property WipeId As String
		Get
			If Me._wipeId Is Nothing Then
				Me._wipeId = SingletonComponent(Of ServerMgr).Instance.persistance.GetUserWipeId(Me.userID)
			End If
			Return Me._wipeId
		End Get
	End Property

	' Token: 0x0600068B RID: 1675 RVA: 0x0004E3E1 File Offset: 0x0004C5E1
	Public Sub DirtyPlayerState()
		Me._playerStateDirty = True
	End Sub

	' Token: 0x0600068C RID: 1676 RVA: 0x0004E3EA File Offset: 0x0004C5EA
	Public Sub SavePlayerState()
		If Me._playerStateDirty Then
			Me._playerStateDirty = False
			SingletonComponent(Of ServerMgr).Instance.playerStateManager.Save(Me.userID)
		End If
	End Sub

	' Token: 0x0600068D RID: 1677 RVA: 0x0004E418 File Offset: 0x0004C618
	Public Sub ResetPlayerState()
		SingletonComponent(Of ServerMgr).Instance.playerStateManager.Reset(Me.userID)
		MyBase.ClientRPC(Of Single)(RpcTarget.Player("SetHostileLength", Me), 0F)
		Me.SendMarkersToClient()
		Me.WipeMissions()
		Me.MissionDirty(True)
	End Sub

	' Token: 0x0600068E RID: 1678 RVA: 0x0004E468 File Offset: 0x0004C668
	Public Function IsSleeping() As Boolean
		Return Me.HasPlayerFlag(Global.BasePlayer.PlayerFlags.Sleeping)
	End Function

	' Token: 0x0600068F RID: 1679 RVA: 0x0004E472 File Offset: 0x0004C672
	Public Function IsSpectating() As Boolean
		Return Me.HasPlayerFlag(Global.BasePlayer.PlayerFlags.Spectating)
	End Function

	' Token: 0x06000690 RID: 1680 RVA: 0x0004E47C File Offset: 0x0004C67C
	Public Function IsRelaxed() As Boolean
		Return Me.HasPlayerFlag(Global.BasePlayer.PlayerFlags.Relaxed)
	End Function

	' Token: 0x06000691 RID: 1681 RVA: 0x0004E489 File Offset: 0x0004C689
	Public Function IsServerFalling() As Boolean
		Return Me.HasPlayerFlag(Global.BasePlayer.PlayerFlags.ServerFall)
	End Function

	' Token: 0x06000692 RID: 1682 RVA: 0x0004E496 File Offset: 0x0004C696
	Public Function IsLoadingAfterTransfer() As Boolean
		Return Me.HasPlayerFlag(Global.BasePlayer.PlayerFlags.LoadingAfterTransfer)
	End Function

	' Token: 0x06000693 RID: 1683 RVA: 0x0004E4A4 File Offset: 0x0004C6A4
	Public Function CanBuild() As Boolean
		If Me.IsBuildingBlockedByVehicle() Then
			Return False
		End If
		If Me.IsBuildingBlockedByEntity() Then
			Return False
		End If
		Dim buildingPrivilege As BuildingPrivlidge = Me.GetBuildingPrivilege()
		Return buildingPrivilege Is Nothing OrElse buildingPrivilege.IsAuthed(Me)
	End Function

	' Token: 0x06000694 RID: 1684 RVA: 0x0004E4E0 File Offset: 0x0004C6E0
	Public Function CanBuild(position As Vector3, rotation As Quaternion, bounds As Bounds) As Boolean
		Dim obb As OBB = New OBB(position, rotation, bounds)
		If Me.IsBuildingBlockedByVehicle(obb) Then
			Return False
		End If
		If Me.IsBuildingBlockedByEntity(obb) Then
			Return False
		End If
		Dim buildingPrivilege As BuildingPrivlidge = MyBase.GetBuildingPrivilege(obb)
		Return buildingPrivilege Is Nothing OrElse buildingPrivilege.IsAuthed(Me)
	End Function

	' Token: 0x06000695 RID: 1685 RVA: 0x0004E528 File Offset: 0x0004C728
	Public Function CanBuild(obb As OBB) As Boolean
		If Me.IsBuildingBlockedByVehicle(obb) Then
			Return False
		End If
		If Me.IsBuildingBlockedByEntity(obb) Then
			Return False
		End If
		Dim buildingPrivilege As BuildingPrivlidge = MyBase.GetBuildingPrivilege(obb)
		Return buildingPrivilege Is Nothing OrElse buildingPrivilege.IsAuthed(Me)
	End Function

	' Token: 0x06000696 RID: 1686 RVA: 0x0004E568 File Offset: 0x0004C768
	Public Function IsBuildingBlocked() As Boolean
		If Me.IsBuildingBlockedByVehicle() Then
			Return True
		End If
		If Me.IsBuildingBlockedByEntity() Then
			Return True
		End If
		Dim buildingPrivilege As BuildingPrivlidge = Me.GetBuildingPrivilege()
		Return Not(buildingPrivilege Is Nothing) AndAlso Not buildingPrivilege.IsAuthed(Me)
	End Function

	' Token: 0x06000697 RID: 1687 RVA: 0x0004E5A8 File Offset: 0x0004C7A8
	Public Function IsBuildingBlocked(position As Vector3, rotation As Quaternion, bounds As Bounds) As Boolean
		Dim obb As OBB = New OBB(position, rotation, bounds)
		If Me.IsBuildingBlockedByVehicle(obb) Then
			Return True
		End If
		If Me.IsBuildingBlockedByEntity(obb) Then
			Return True
		End If
		Dim buildingPrivilege As BuildingPrivlidge = MyBase.GetBuildingPrivilege(obb)
		Return Not(buildingPrivilege Is Nothing) AndAlso Not buildingPrivilege.IsAuthed(Me)
	End Function

	' Token: 0x06000698 RID: 1688 RVA: 0x0004E5F4 File Offset: 0x0004C7F4
	Public Function IsBuildingBlocked(obb As OBB) As Boolean
		If Me.IsBuildingBlockedByVehicle(obb) Then
			Return True
		End If
		If Me.IsBuildingBlockedByEntity(obb) Then
			Return True
		End If
		Dim buildingPrivilege As BuildingPrivlidge = MyBase.GetBuildingPrivilege(obb)
		Return Not(buildingPrivilege Is Nothing) AndAlso Not buildingPrivilege.IsAuthed(Me)
	End Function

	' Token: 0x06000699 RID: 1689 RVA: 0x0004E634 File Offset: 0x0004C834
	Public Function IsBuildingAuthed() As Boolean
		If Me.IsBuildingBlockedByVehicle() Then
			Return False
		End If
		If Me.IsBuildingBlockedByEntity() Then
			Return False
		End If
		Dim buildingPrivilege As BuildingPrivlidge = Me.GetBuildingPrivilege()
		Return Not(buildingPrivilege Is Nothing) AndAlso buildingPrivilege.IsAuthed(Me)
	End Function

	' Token: 0x0600069A RID: 1690 RVA: 0x0004E670 File Offset: 0x0004C870
	Public Function IsBuildingAuthed(position As Vector3, rotation As Quaternion, bounds As Bounds) As Boolean
		Dim obb As OBB = New OBB(position, rotation, bounds)
		If Me.IsBuildingBlockedByVehicle(obb) Then
			Return False
		End If
		If Me.IsBuildingBlockedByEntity(obb) Then
			Return False
		End If
		Dim buildingPrivilege As BuildingPrivlidge = MyBase.GetBuildingPrivilege(obb)
		Return Not(buildingPrivilege Is Nothing) AndAlso buildingPrivilege.IsAuthed(Me)
	End Function

	' Token: 0x0600069B RID: 1691 RVA: 0x0004E6B8 File Offset: 0x0004C8B8
	Public Function IsBuildingAuthed(obb As OBB) As Boolean
		If Me.IsBuildingBlockedByVehicle(obb) Then
			Return False
		End If
		If Me.IsBuildingBlockedByEntity(obb) Then
			Return False
		End If
		Dim buildingPrivilege As BuildingPrivlidge = MyBase.GetBuildingPrivilege(obb)
		Return Not(buildingPrivilege Is Nothing) AndAlso buildingPrivilege.IsAuthed(Me)
	End Function

	' Token: 0x0600069C RID: 1692 RVA: 0x0004E6F5 File Offset: 0x0004C8F5
	Public Function CanPlaceBuildingPrivilege() As Boolean
		Return Not Me.IsBuildingBlockedByVehicle() AndAlso Not Me.IsBuildingBlockedByEntity() AndAlso Me.GetBuildingPrivilege() Is Nothing
	End Function

	' Token: 0x0600069D RID: 1693 RVA: 0x0004E718 File Offset: 0x0004C918
	Public Function CanPlaceBuildingPrivilege(position As Vector3, rotation As Quaternion, bounds As Bounds) As Boolean
		Dim obb As OBB = New OBB(position, rotation, bounds)
		Return Not Me.IsBuildingBlockedByVehicle(obb) AndAlso Not Me.IsBuildingBlockedByEntity(obb) AndAlso MyBase.GetBuildingPrivilege(obb) Is Nothing
	End Function

	' Token: 0x0600069E RID: 1694 RVA: 0x0004E752 File Offset: 0x0004C952
	Public Function CanPlaceBuildingPrivilege(obb As OBB) As Boolean
		Return Not Me.IsBuildingBlockedByVehicle(obb) AndAlso Not Me.IsBuildingBlockedByEntity(obb) AndAlso MyBase.GetBuildingPrivilege(obb) Is Nothing
	End Function

	' Token: 0x0600069F RID: 1695 RVA: 0x0004E778 File Offset: 0x0004C978
	Public Function IsNearEnemyBase() As Boolean
		If Me.IsBuildingBlockedByVehicle() Then
			Return True
		End If
		If Me.IsBuildingBlockedByEntity() Then
			Return True
		End If
		Dim buildingPrivilege As BuildingPrivlidge = Me.GetBuildingPrivilege()
		Return Not(buildingPrivilege Is Nothing) AndAlso Not buildingPrivilege.IsAuthed(Me) AndAlso buildingPrivilege.AnyAuthed()
	End Function

	' Token: 0x060006A0 RID: 1696 RVA: 0x0004E7BC File Offset: 0x0004C9BC
	Public Function IsNearEnemyBase(position As Vector3, rotation As Quaternion, bounds As Bounds) As Boolean
		Dim obb As OBB = New OBB(position, rotation, bounds)
		If Me.IsBuildingBlockedByVehicle(obb) Then
			Return True
		End If
		If Me.IsBuildingBlockedByEntity(obb) Then
			Return True
		End If
		Dim buildingPrivilege As BuildingPrivlidge = MyBase.GetBuildingPrivilege(obb)
		Return Not(buildingPrivilege Is Nothing) AndAlso Not buildingPrivilege.IsAuthed(Me) AndAlso buildingPrivilege.AnyAuthed()
	End Function

	' Token: 0x060006A1 RID: 1697 RVA: 0x0004E810 File Offset: 0x0004CA10
	Public Function IsNearEnemyBase(obb As OBB) As Boolean
		If Me.IsBuildingBlockedByVehicle(obb) Then
			Return True
		End If
		If Me.IsBuildingBlockedByEntity(obb) Then
			Return True
		End If
		Dim buildingPrivilege As BuildingPrivlidge = MyBase.GetBuildingPrivilege(obb)
		Return Not(buildingPrivilege Is Nothing) AndAlso Not buildingPrivilege.IsAuthed(Me) AndAlso buildingPrivilege.AnyAuthed()
	End Function

	' Token: 0x060006A2 RID: 1698 RVA: 0x0004E857 File Offset: 0x0004CA57
	Public Function IsBuildingBlockedByVehicle() As Boolean
		Return Me.IsBuildingBlockedByVehicle(Me.WorldSpaceBounds())
	End Function

	' Token: 0x060006A3 RID: 1699 RVA: 0x0004E865 File Offset: 0x0004CA65
	Public Function IsBuildingBlockedByEntity() As Boolean
		Return Me.IsBuildingBlockedByEntity(Me.WorldSpaceBounds())
	End Function

	' Token: 0x060006A4 RID: 1700 RVA: 0x0004E874 File Offset: 0x0004CA74
	Public Function HasPrivilegeFromOther() As Boolean
		If UnityEngine.Time.time - Me.cachedPrivilegeFromOtherTime > 1F Then
			Me.cachedPrivilegeFromOtherTime = UnityEngine.Time.time
			Me.cachedPrivilegeFromOther = Nothing
			Me.IsBuildingBlockedByEntity(Me.WorldSpaceBounds())
			Me.IsBuildingBlockedByVehicle(Me.WorldSpaceBounds())
		End If
		Return Me.cachedPrivilegeFromOther IsNot Nothing
	End Function

	' Token: 0x060006A5 RID: 1701 RVA: 0x0004E8CC File Offset: 0x0004CACC
	Private Function IsBuildingBlockedByVehicle(obb As OBB) As Boolean
		Dim list As List(Of Global.BaseVehicle) = Facepunch.Pool.GetList(Of Global.BaseVehicle)()
		Global.Vis.Entities(Of Global.BaseVehicle)(obb.position, 2F + obb.extents.magnitude, list, 134217728, QueryTriggerInteraction.Collide)
		For i As Integer = 0 To list.Count - 1
			Dim baseVehicle As Global.BaseVehicle = list(i)
			If baseVehicle.isServer = MyBase.isServer AndAlso Not baseVehicle.IsDead() AndAlso obb.Distance(baseVehicle.WorldSpaceBounds()) <= 2F Then
				If Not baseVehicle.IsAuthed(Me) Then
					Facepunch.Pool.FreeList(Of Global.BaseVehicle)(list)
					Return True
				End If
				Me.cachedPrivilegeFromOther = baseVehicle
			End If
		Next
		Facepunch.Pool.FreeList(Of Global.BaseVehicle)(list)
		Return False
	End Function

	' Token: 0x060006A6 RID: 1702 RVA: 0x0004E96C File Offset: 0x0004CB6C
	Private Function IsBuildingBlockedByEntity(obb As OBB) As Boolean
		Dim list As List(Of Global.BaseEntity) = Facepunch.Pool.GetList(Of Global.BaseEntity)()
		Global.Vis.Entities(Of Global.BaseEntity)(obb.position, 3F + obb.extents.magnitude, list, 2097152, QueryTriggerInteraction.Collide)
		For i As Integer = 0 To list.Count - 1
			Dim baseEntity As Global.BaseEntity = list(i)
			If baseEntity.isServer = MyBase.isServer AndAlso obb.Distance(baseEntity.WorldSpaceBounds()) <= 3F Then
				Dim entityBuildingPrivilege As EntityPrivilege = baseEntity.GetEntityBuildingPrivilege()
				If Not(entityBuildingPrivilege Is Nothing) Then
					If Not entityBuildingPrivilege.IsAuthed(Me) Then
						Facepunch.Pool.FreeList(Of Global.BaseEntity)(list)
						Return True
					End If
					Me.cachedPrivilegeFromOther = baseEntity
				End If
			End If
		Next
		Facepunch.Pool.FreeList(Of Global.BaseEntity)(list)
		Return False
	End Function

	' Token: 0x060006A7 RID: 1703 RVA: 0x0004EA14 File Offset: 0x0004CC14
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.FromOwner()>
	Public Sub OnProjectileAttack(msg As Global.BaseEntity.RPCMessage)
		Dim playerProjectileAttack As PlayerProjectileAttack = PlayerProjectileAttack.Deserialize(msg.read)
		If playerProjectileAttack Is Nothing Then
			Return
		End If
		Dim playerAttack As PlayerAttack = playerProjectileAttack.playerAttack
		Dim hitInfo As HitInfo = New HitInfo()
		hitInfo.LoadFromAttack(playerAttack.attack, True)
		hitInfo.Initiator = Me
		hitInfo.ProjectileID = playerAttack.projectileID
		hitInfo.ProjectileDistance = playerProjectileAttack.hitDistance
		hitInfo.ProjectileVelocity = playerProjectileAttack.hitVelocity
		hitInfo.ProjectileTravelTime = playerProjectileAttack.travelTime
		hitInfo.Predicted = msg.connection
		If hitInfo.IsNaNOrInfinity() OrElse Single.IsNaN(playerProjectileAttack.travelTime) OrElse Single.IsInfinity(playerProjectileAttack.travelTime) Then
			Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, "Contains NaN (" + playerAttack.projectileID.ToString() + ")", True)
			playerProjectileAttack.ResetToPool()
			Me.stats.combat.LogInvalid(hitInfo, "projectile_nan")
			Return
		End If
		Dim firedProjectile As Global.BasePlayer.FiredProjectile
		If Not Me.firedProjectiles.TryGetValue(playerAttack.projectileID, firedProjectile) Then
			Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, "Missing ID (" + playerAttack.projectileID.ToString() + ")", False)
			playerProjectileAttack.ResetToPool()
			Me.stats.combat.LogInvalid(hitInfo, "projectile_invalid")
			Return
		End If
		hitInfo.ProjectileHits = firedProjectile.hits
		hitInfo.ProjectileIntegrity = firedProjectile.integrity
		hitInfo.ProjectileTrajectoryMismatch = firedProjectile.trajectoryMismatch
		If firedProjectile.integrity <= 0F Then
			Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, "Integrity is zero (" + playerAttack.projectileID.ToString() + ")", True)
			Analytics.Azure.OnProjectileHackViolation(firedProjectile)
			playerProjectileAttack.ResetToPool()
			Me.stats.combat.LogInvalid(hitInfo, "projectile_integrity")
			Return
		End If
		If firedProjectile.firedTime < UnityEngine.Time.realtimeSinceStartup - 8F Then
			Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, "Lifetime is zero (" + playerAttack.projectileID.ToString() + ")", True)
			Analytics.Azure.OnProjectileHackViolation(firedProjectile)
			playerProjectileAttack.ResetToPool()
			Me.stats.combat.LogInvalid(hitInfo, "projectile_lifetime")
			Return
		End If
		If firedProjectile.ricochets > 0 Then
			Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, "Projectile is ricochet (" + playerAttack.projectileID.ToString() + ")", True)
			Analytics.Azure.OnProjectileHackViolation(firedProjectile)
			playerProjectileAttack.ResetToPool()
			Me.stats.combat.LogInvalid(hitInfo, "projectile_ricochet")
			Return
		End If
		hitInfo.Weapon = firedProjectile.weaponSource
		hitInfo.WeaponPrefab = firedProjectile.weaponPrefab
		hitInfo.ProjectilePrefab = firedProjectile.projectilePrefab
		hitInfo.damageProperties = firedProjectile.projectilePrefab.damageProperties
		Dim position As Vector3 = firedProjectile.position
		Dim initialPositionOffset As Vector3 = firedProjectile.initialPositionOffset
		Dim positionOffset As Vector3 = firedProjectile.positionOffset
		Dim velocity As Vector3 = firedProjectile.velocity
		Dim partialTime As Single = firedProjectile.partialTime
		Dim travelTime As Single = firedProjectile.travelTime
		Dim num As Single = Mathf.Clamp(playerProjectileAttack.travelTime, firedProjectile.travelTime, 8F)
		Dim gravity As Vector3 = UnityEngine.Physics.gravity * firedProjectile.projectilePrefab.gravityModifier
		Dim drag As Single = firedProjectile.projectilePrefab.drag
		Dim hitEntity As Global.BaseEntity = hitInfo.HitEntity
		Dim basePlayer As Global.BasePlayer = TryCast(hitEntity, Global.BasePlayer)
		Dim flag As Boolean = basePlayer IsNot Nothing
		Dim flag2 As Boolean = flag AndAlso basePlayer.IsSleeping()
		Dim flag3 As Boolean = flag AndAlso basePlayer.IsWounded()
		Dim flag4 As Boolean = flag AndAlso basePlayer.isMounted
		Dim flag5 As Boolean = flag AndAlso basePlayer.HasParent()
		Dim flag6 As Boolean = hitEntity IsNot Nothing
		Dim flag7 As Boolean = flag6 AndAlso hitEntity.IsNpc
		Dim flag8 As Boolean = hitInfo.HitMaterial = Projectile.WaterMaterialID()
		If firedProjectile.protection > 0 Then
			Dim flag9 As Boolean = True
			Dim num2 As Single = 1F + ConVar.AntiHack.projectile_forgiveness
			Dim num3 As Single = 1F - ConVar.AntiHack.projectile_forgiveness
			Dim projectile_clientframes As Single = ConVar.AntiHack.projectile_clientframes
			Dim projectile_serverframes As Single = ConVar.AntiHack.projectile_serverframes
			Dim num4 As Single = Mathx.Decrement(firedProjectile.firedTime)
			Dim num5 As Single = Mathf.Clamp(Mathx.Increment(UnityEngine.Time.realtimeSinceStartup) - num4, 0F, 8F)
			Dim num6 As Single = num
			Dim num7 As Single = Mathf.Abs(num5 - num6)
			firedProjectile.desyncLifeTime = num7
			Dim num8 As Single = Mathf.Min(num5, num6)
			Dim num9 As Single = projectile_clientframes / 60F
			Dim num10 As Single = projectile_serverframes * Mathx.Max(UnityEngine.Time.deltaTime, UnityEngine.Time.smoothDeltaTime, UnityEngine.Time.fixedDeltaTime)
			Dim num11 As Single = (Me.desyncTimeClamped + num8 + num9 + num10) * num2
			Dim num12 As Single = If((firedProjectile.protection >= 6), ((Me.desyncTimeClamped + num9 + num10) * num2), num11)
			Dim num13 As Single = (num5 - Me.desyncTimeClamped - num9 - num10) * num3
			Dim num14 As Single = Vector3.Distance(firedProjectile.initialPosition, hitInfo.HitPositionWorld)
			Dim num15 As Integer = 1075904512
			If ConVar.AntiHack.projectile_terraincheck Then
				num15 = num15 Or 8388608
			End If
			If ConVar.AntiHack.projectile_vehiclecheck Then
				num15 = num15 Or 134217728
			End If
			If flag AndAlso hitInfo.boneArea = CType((-1), HitArea) Then
				Dim name As String = hitInfo.ProjectilePrefab.name
				Dim text As String = If(flag6, hitEntity.ShortPrefabName, "world")
				Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, String.Concat(New String() { "Bone is invalid (", name, " on ", text, " bone ", hitInfo.HitBone.ToString(), ")" }), True)
				Me.stats.combat.LogInvalid(hitInfo, "projectile_bone")
				flag9 = False
			End If
			If flag8 Then
				If flag6 Then
					Dim name2 As String = hitInfo.ProjectilePrefab.name
					Dim text2 As String = If(flag6, hitEntity.ShortPrefabName, "world")
					Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, String.Concat(New String() { "Projectile water hit on entity (", name2, " on ", text2, ")" }), True)
					Analytics.Azure.OnProjectileHackViolation(firedProjectile)
					Me.stats.combat.LogInvalid(hitInfo, "water_entity")
					flag9 = False
				End If
				If Not WaterLevel.Test(hitInfo.HitPositionWorld - 0.5F * Vector3.up, True, True, Me) Then
					Dim name3 As String = hitInfo.ProjectilePrefab.name
					Dim text3 As String = If(flag6, hitEntity.ShortPrefabName, "world")
					Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, String.Concat(New String() { "Projectile water level (", name3, " on ", text3, ")" }), True)
					Analytics.Azure.OnProjectileHackViolation(firedProjectile)
					Me.stats.combat.LogInvalid(hitInfo, "water_level")
					flag9 = False
				End If
			End If
			If firedProjectile.protection >= 2 Then
				If flag6 OrElse (firedProjectile.protection < 6 AndAlso flag) Then
					Dim num16 As Single = hitEntity.MaxVelocity() + hitEntity.GetParentVelocity().magnitude
					Dim num17 As Single = hitEntity.BoundsPadding() + num12 * num16
					Dim num18 As Single = hitEntity.Distance(hitInfo.HitPositionWorld)
					If num18 > num17 Then
						Dim name4 As String = hitInfo.ProjectilePrefab.name
						Dim shortPrefabName As String = hitEntity.ShortPrefabName
						Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, String.Concat(New String() { "Entity too far away (", name4, " on ", shortPrefabName, " with ", num18.ToString(), "m > ", num17.ToString(), "m in ", num12.ToString(), "s)" }), True)
						Analytics.Azure.OnProjectileHackViolation(firedProjectile)
						Me.stats.combat.LogInvalid(hitInfo, "entity_distance")
						flag9 = False
					End If
				End If
				If firedProjectile.protection >= 6 AndAlso flag9 AndAlso flag AndAlso Not flag7 AndAlso Not flag2 AndAlso Not flag3 AndAlso Not flag4 AndAlso Not flag5 Then
					Dim magnitude As Single = basePlayer.GetParentVelocity().magnitude
					Dim num19 As Single = basePlayer.BoundsPadding() + num12 * magnitude + ConVar.AntiHack.tickhistoryforgiveness
					Dim num20 As Single = basePlayer.tickHistory.Distance(basePlayer, hitInfo.HitPositionWorld)
					If num20 > num19 Then
						Dim name5 As String = hitInfo.ProjectilePrefab.name
						Dim shortPrefabName2 As String = basePlayer.ShortPrefabName
						Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, String.Concat(New String() { "Player too far away (", name5, " on ", shortPrefabName2, " with ", num20.ToString(), "m > ", num19.ToString(), "m in ", num12.ToString(), "s)" }), True)
						Analytics.Azure.OnProjectileHackViolation(firedProjectile)
						Me.stats.combat.LogInvalid(hitInfo, "player_distance")
						flag9 = False
					End If
				End If
			End If
			If firedProjectile.protection >= 1 Then
				Dim num21 As Single = If(flag6, (hitEntity.MaxVelocity() + hitEntity.GetParentVelocity().magnitude), 0F)
				Dim num22 As Single = If(flag6, (num12 * num21), 0F)
				Dim magnitude2 As Single = firedProjectile.initialVelocity.magnitude
				Dim num23 As Single = hitInfo.ProjectilePrefab.initialDistance + num11 * magnitude2
				Dim num24 As Single = hitInfo.ProjectileDistance + 1F + positionOffset.magnitude + num22 + Me.estimatedVelocity.magnitude
				If num14 > num23 Then
					Dim name6 As String = hitInfo.ProjectilePrefab.name
					Dim text4 As String = If(flag6, hitEntity.ShortPrefabName, "world")
					Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, String.Concat(New String() { "Projectile too fast (", name6, " on ", text4, " with ", num14.ToString(), "m > ", num23.ToString(), "m in ", num11.ToString(), "s)" }), True)
					Analytics.Azure.OnProjectileHackViolation(firedProjectile)
					Me.stats.combat.LogInvalid(hitInfo, "projectile_maxspeed")
					flag9 = False
				End If
				If num14 > num24 Then
					Dim name7 As String = hitInfo.ProjectilePrefab.name
					Dim text5 As String = If(flag6, hitEntity.ShortPrefabName, "world")
					Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, String.Concat(New String() { "Projectile too far away (", name7, " on ", text5, " with ", num14.ToString(), "m > ", num24.ToString(), "m in ", num11.ToString(), "s)" }), True)
					Analytics.Azure.OnProjectileHackViolation(firedProjectile)
					Me.stats.combat.LogInvalid(hitInfo, "projectile_distance")
					flag9 = False
				End If
				If num7 > ConVar.AntiHack.projectile_desync Then
					Dim name8 As String = hitInfo.ProjectilePrefab.name
					Dim text6 As String = If(flag6, hitEntity.ShortPrefabName, "world")
					Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, String.Concat(New String() { "Projectile desync (", name8, " on ", text6, " with ", num7.ToString(), "s > ", ConVar.AntiHack.projectile_desync.ToString(), "s)" }), True)
					Analytics.Azure.OnProjectileHackViolation(firedProjectile)
					Me.stats.combat.LogInvalid(hitInfo, "projectile_desync")
					flag9 = False
				End If
			End If
			If firedProjectile.protection >= 4 Then
				Dim num25 As Single = 0F
				If flag6 Then
					Dim num26 As Single = hitEntity.GetParentVelocity().magnitude
					If TypeOf hitEntity Is Global.CargoShip OrElse TypeOf hitEntity Is Tugboat Then
						num26 += hitEntity.MaxVelocity()
					End If
					num25 = num12 * num26
				End If
				Dim a As Vector3
				Dim b As Vector3
				Me.SimulateProjectile(position, velocity, partialTime, num - travelTime, gravity, drag, a, b)
				Dim line As Line = New Line(a - b, position + b)
				Dim num27 As Single = Mathf.Max(line.Distance(hitInfo.PointStart) - initialPositionOffset.magnitude - num25, 0F)
				Dim num28 As Single = Mathf.Max(line.Distance(hitInfo.HitPositionWorld) - initialPositionOffset.magnitude - num25, 0F)
				If num27 > ConVar.AntiHack.projectile_trajectory Then
					Dim name9 As String = firedProjectile.projectilePrefab.name
					Dim text7 As String = If(flag6, hitEntity.ShortPrefabName, "world")
					Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, String.Concat(New String() { "Start position trajectory (", name9, " on ", text7, " with ", num27.ToString(), "m > ", ConVar.AntiHack.projectile_trajectory.ToString(), "m)" }), True)
					Analytics.Azure.OnProjectileHackViolation(firedProjectile)
					Me.stats.combat.LogInvalid(hitInfo, "trajectory_start")
					flag9 = False
				End If
				If num28 > ConVar.AntiHack.projectile_trajectory Then
					Dim name10 As String = firedProjectile.projectilePrefab.name
					Dim text8 As String = If(flag6, hitEntity.ShortPrefabName, "world")
					Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, String.Concat(New String() { "End position trajectory (", name10, " on ", text8, " with ", num28.ToString(), "m > ", ConVar.AntiHack.projectile_trajectory.ToString(), "m)" }), True)
					Analytics.Azure.OnProjectileHackViolation(firedProjectile)
					Me.stats.combat.LogInvalid(hitInfo, "trajectory_end")
					flag9 = False
				End If
				If hitInfo.ProjectileTrajectoryMismatch > ConVar.AntiHack.projectile_trajectory Then
					Dim name11 As String = firedProjectile.projectilePrefab.name
					Dim text9 As String = If(flag6, hitEntity.ShortPrefabName, "world")
					Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, String.Concat(New String() { "Update position trajectory (", name11, " on ", text9, " with ", hitInfo.ProjectileTrajectoryMismatch.ToString(), "m > ", ConVar.AntiHack.projectile_trajectory.ToString(), "m)" }), True)
					Analytics.Azure.OnProjectileHackViolation(firedProjectile)
					Me.stats.combat.LogInvalid(hitInfo, "trajectory_update_total")
					flag9 = False
				End If
				hitInfo.ProjectileVelocity = velocity
				If playerProjectileAttack.hitVelocity <> Vector3.zero AndAlso velocity <> Vector3.zero Then
					Dim num29 As Single = Vector3.Angle(playerProjectileAttack.hitVelocity, velocity)
					Dim num30 As Single = playerProjectileAttack.hitVelocity.magnitude / velocity.magnitude
					If num29 > ConVar.AntiHack.projectile_anglechange Then
						Dim name12 As String = firedProjectile.projectilePrefab.name
						Dim text10 As String = If(flag6, hitEntity.ShortPrefabName, "world")
						Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, String.Concat(New String() { "Trajectory angle change (", name12, " on ", text10, " with ", num29.ToString(), "deg > ", ConVar.AntiHack.projectile_anglechange.ToString(), "deg)" }), True)
						Analytics.Azure.OnProjectileHackViolation(firedProjectile)
						Me.stats.combat.LogInvalid(hitInfo, "angle_change")
						flag9 = False
					End If
					If num30 > ConVar.AntiHack.projectile_velocitychange Then
						Dim name13 As String = firedProjectile.projectilePrefab.name
						Dim text11 As String = If(flag6, hitEntity.ShortPrefabName, "world")
						Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, String.Concat(New String() { "Trajectory velocity change (", name13, " on ", text11, " with ", num30.ToString(), " > ", ConVar.AntiHack.projectile_velocitychange.ToString(), ")" }), True)
						Analytics.Azure.OnProjectileHackViolation(firedProjectile)
						Me.stats.combat.LogInvalid(hitInfo, "velocity_change")
						flag9 = False
					End If
				End If
				Dim magnitude3 As Single = velocity.magnitude
				Dim num31 As Single = num13 * magnitude3
				If num14 < num31 Then
					Dim name14 As String = hitInfo.ProjectilePrefab.name
					Dim text12 As String = If(flag6, hitEntity.ShortPrefabName, "world")
					Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, String.Concat(New String() { "Projectile too slow (", name14, " on ", text12, " with ", num14.ToString(), "m < ", num31.ToString(), "m in ", num13.ToString(), "s)" }), True)
					Analytics.Azure.OnProjectileHackViolation(firedProjectile)
					Me.stats.combat.LogInvalid(hitInfo, "projectile_minspeed")
					flag9 = False
				End If
			End If
			If firedProjectile.protection >= 3 Then
				Dim position2 As Vector3 = firedProjectile.position
				Dim pointStart As Vector3 = hitInfo.PointStart
				Dim vector As Vector3 = hitInfo.HitPositionWorld
				If Not flag8 Then
					vector -= hitInfo.ProjectileVelocity.normalized * 0.001F
				End If
				Dim vector2 As Vector3 = hitInfo.PositionOnRay(vector)
				Dim b2 As Vector3 = Vector3.zero
				Dim b3 As Vector3 = Vector3.zero
				If ConVar.AntiHack.projectile_backtracking > 0F Then
					b2 = (pointStart - position2).normalized * ConVar.AntiHack.projectile_backtracking
					b3 = (vector2 - pointStart).normalized * ConVar.AntiHack.projectile_backtracking
				End If
				Dim flag10 As Boolean = GamePhysics.LineOfSight(position2 - b2, pointStart + b2, num15, firedProjectile.lastEntityHit) AndAlso GamePhysics.LineOfSight(pointStart - b3, vector2, num15, firedProjectile.lastEntityHit) AndAlso GamePhysics.LineOfSight(vector2, vector, num15, firedProjectile.lastEntityHit)
				Dim flag11 As Boolean = True
				If flag10 Then
					flag11 = (GamePhysics.LineOfSight(position2, vector, num15, firedProjectile.lastEntityHit) AndAlso GamePhysics.LineOfSight(vector, position2, num15, firedProjectile.lastEntityHit))
				End If
				Dim flag12 As Boolean = True
				If flag10 Then
					Dim simulatedPositions As List(Of Vector3) = firedProjectile.simulatedPositions
					If simulatedPositions.Count > ConVar.AntiHack.projectile_update_limit Then
						flag12 = False
					Else
						simulatedPositions.Add(position2)
						For i As Integer = 1 To simulatedPositions.Count - 1
							If Not GamePhysics.LineOfSight(simulatedPositions(i - 1), simulatedPositions(i), num15, firedProjectile.lastEntityHit) OrElse Not GamePhysics.LineOfSight(simulatedPositions(i), simulatedPositions(i - 1), num15, firedProjectile.lastEntityHit) Then
								flag12 = False
								Exit For
							End If
						Next
					End If
				End If
				Dim flag13 As Boolean = flag10 AndAlso ((firedProjectile.simulatedPositions.Count > 1 AndAlso flag12) OrElse (firedProjectile.simulatedPositions.Count <= 1 AndAlso flag11))
				If Not flag13 Then
					Me.stats.Add("hit_" + If(flag6, hitEntity.Categorize(), "world") + "_indirect_los", 1, Global.Stats.Server)
				Else
					Me.stats.Add("hit_" + If(flag6, hitEntity.Categorize(), "world") + "_direct_los", 1, Global.Stats.Server)
				End If
				If Not flag13 Then
					Dim name15 As String = hitInfo.ProjectilePrefab.name
					Dim text13 As String = If(flag6, hitEntity.ShortPrefabName, "world")
					Dim description As String = If((Not flag10), "projectile_los", "projectile_los_detailed")
					Dim type As AntiHackType = AntiHackType.ProjectileHack
					Dim array As String() = New String(11) {}
					array(0) = "Line of sight ("
					array(1) = name15
					array(2) = " on "
					array(3) = text13
					array(4) = ") "
					Dim num32 As Integer = 5
					Dim vector3 As Vector3 = position2
					array(num32) = vector3.ToString()
					array(6) = " "
					Dim num33 As Integer = 7
					vector3 = pointStart
					array(num33) = vector3.ToString()
					array(8) = " "
					Dim num34 As Integer = 9
					vector3 = vector2
					array(num34) = vector3.ToString()
					array(10) = " "
					Dim num35 As Integer = 11
					vector3 = vector
					array(num35) = vector3.ToString()
					Global.AntiHack.Log(Me, type, String.Concat(array), True)
					Analytics.Azure.OnProjectileHackViolation(firedProjectile)
					Me.stats.combat.LogInvalid(hitInfo, description)
					flag9 = False
				End If
				If flag9 AndAlso flag AndAlso Not flag7 Then
					Dim hitPositionWorld As Vector3 = hitInfo.HitPositionWorld
					Dim position3 As Vector3 = basePlayer.eyes.position
					Dim vector4 As Vector3 = basePlayer.CenterPoint()
					Dim projectile_losforgiveness As Single = ConVar.AntiHack.projectile_losforgiveness
					Dim flag14 As Boolean = GamePhysics.LineOfSight(hitPositionWorld, position3, num15, 0F, projectile_losforgiveness, Nothing) AndAlso GamePhysics.LineOfSight(position3, hitPositionWorld, num15, projectile_losforgiveness, 0F, Nothing)
					If Not flag14 Then
						flag14 = (GamePhysics.LineOfSight(hitPositionWorld, vector4, num15, 0F, projectile_losforgiveness, Nothing) AndAlso GamePhysics.LineOfSight(vector4, hitPositionWorld, num15, projectile_losforgiveness, 0F, Nothing))
					End If
					If Not flag14 Then
						Dim name16 As String = hitInfo.ProjectilePrefab.name
						Dim text14 As String = If(flag6, hitEntity.ShortPrefabName, "world")
						Dim type2 As AntiHackType = AntiHackType.ProjectileHack
						Dim array2 As String() = New String(11) {}
						array2(0) = "Line of sight ("
						array2(1) = name16
						array2(2) = " on "
						array2(3) = text14
						array2(4) = ") "
						Dim num36 As Integer = 5
						Dim vector3 As Vector3 = hitPositionWorld
						array2(num36) = vector3.ToString()
						array2(6) = " "
						Dim num37 As Integer = 7
						vector3 = position3
						array2(num37) = vector3.ToString()
						array2(8) = " or "
						Dim num38 As Integer = 9
						vector3 = hitPositionWorld
						array2(num38) = vector3.ToString()
						array2(10) = " "
						Dim num39 As Integer = 11
						vector3 = vector4
						array2(num39) = vector3.ToString()
						Global.AntiHack.Log(Me, type2, String.Concat(array2), True)
						Analytics.Azure.OnProjectileHackViolation(firedProjectile)
						Me.stats.combat.LogInvalid(hitInfo, "projectile_los")
						flag9 = False
					End If
				End If
			End If
			If Not flag9 Then
				Global.AntiHack.AddViolation(Me, AntiHackType.ProjectileHack, ConVar.AntiHack.projectile_penalty)
				playerProjectileAttack.ResetToPool()
				Return
			End If
		End If
		firedProjectile.position = hitInfo.HitPositionWorld
		firedProjectile.velocity = playerProjectileAttack.hitVelocity
		firedProjectile.travelTime = num
		firedProjectile.partialTime = partialTime
		firedProjectile.hits += 1
		firedProjectile.lastEntityHit = hitEntity
		firedProjectile.simulatedPositions.Clear()
		firedProjectile.simulatedPositions.Add(position)
		hitInfo.ProjectilePrefab.CalculateDamage(hitInfo, firedProjectile.projectileModifier, firedProjectile.integrity)
		If flag8 Then
			If hitInfo.ProjectilePrefab.waterIntegrityLoss > 0F Then
				firedProjectile.integrity = Mathf.Clamp01(firedProjectile.integrity - hitInfo.ProjectilePrefab.waterIntegrityLoss)
			End If
		ElseIf hitInfo.ProjectilePrefab.penetrationPower <= 0F OrElse Not flag6 Then
			firedProjectile.integrity = 0F
		Else
			Dim num40 As Single = hitEntity.PenetrationResistance(hitInfo) / hitInfo.ProjectilePrefab.penetrationPower
			firedProjectile.integrity = Mathf.Clamp01(firedProjectile.integrity - num40)
		End If
		If flag6 Then
			Me.stats.Add(firedProjectile.itemMod.category + "_hit_" + hitEntity.Categorize(), 1, Global.Stats.Steam)
		End If
		If firedProjectile.integrity <= 0F Then
			If firedProjectile.hits <= ConVar.AntiHack.projectile_impactspawndepth Then
				firedProjectile.itemMod.ServerProjectileHit(hitInfo)
			End If
			If hitInfo.ProjectilePrefab.remainInWorld Then
				Me.CreateWorldProjectile(hitInfo, firedProjectile.itemDef, firedProjectile.itemMod, hitInfo.ProjectilePrefab, firedProjectile.pickupItem)
			End If
		ElseIf firedProjectile.hits = ConVar.AntiHack.projectile_impactspawndepth Then
			firedProjectile.itemMod.ServerProjectileHit(hitInfo)
		End If
		Me.firedProjectiles(playerAttack.projectileID) = firedProjectile
		If flag6 Then
			If firedProjectile.hits <= ConVar.AntiHack.projectile_damagedepth Then
				hitEntity.OnAttacked(hitInfo)
			Else
				Me.stats.combat.LogInvalid(hitInfo, "ricochet")
			End If
		End If
		hitInfo.DoHitEffects = hitInfo.ProjectilePrefab.doDefaultHitEffects
		Effect.server.ImpactEffect(hitInfo)
		playerProjectileAttack.ResetToPool()
	End Sub

	' Token: 0x060006A8 RID: 1704 RVA: 0x00050124 File Offset: 0x0004E324
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.FromOwner()>
	Public Sub OnProjectileRicochet(msg As Global.BaseEntity.RPCMessage)
		Dim playerProjectileRicochet As PlayerProjectileRicochet = PlayerProjectileRicochet.Deserialize(msg.read)
		If playerProjectileRicochet Is Nothing Then
			Return
		End If
		If playerProjectileRicochet.hitPosition.IsNaNOrInfinity() OrElse playerProjectileRicochet.inVelocity.IsNaNOrInfinity() OrElse playerProjectileRicochet.outVelocity.IsNaNOrInfinity() OrElse playerProjectileRicochet.hitNormal.IsNaNOrInfinity() OrElse Single.IsNaN(playerProjectileRicochet.travelTime) OrElse Single.IsInfinity(playerProjectileRicochet.travelTime) Then
			Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, "Contains NaN (" + playerProjectileRicochet.projectileID.ToString() + ")", True)
			playerProjectileRicochet.ResetToPool()
			Return
		End If
		Dim firedProjectile As Global.BasePlayer.FiredProjectile
		If Not Me.firedProjectiles.TryGetValue(playerProjectileRicochet.projectileID, firedProjectile) Then
			Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, "Missing ID (" + playerProjectileRicochet.projectileID.ToString() + ")", False)
			playerProjectileRicochet.ResetToPool()
			Return
		End If
		If firedProjectile.firedTime < UnityEngine.Time.realtimeSinceStartup - 8F Then
			Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, "Lifetime is zero (" + playerProjectileRicochet.projectileID.ToString() + ")", True)
			playerProjectileRicochet.ResetToPool()
			Return
		End If
		firedProjectile.ricochets += 1
		Me.firedProjectiles(playerProjectileRicochet.projectileID) = firedProjectile
		playerProjectileRicochet.ResetToPool()
	End Sub

	' Token: 0x060006A9 RID: 1705 RVA: 0x00050260 File Offset: 0x0004E460
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.FromOwner()>
	Public Sub OnProjectileUpdate(msg As Global.BaseEntity.RPCMessage)
		Dim playerProjectileUpdate As PlayerProjectileUpdate = PlayerProjectileUpdate.Deserialize(msg.read)
		If playerProjectileUpdate Is Nothing Then
			Return
		End If
		If playerProjectileUpdate.curPosition.IsNaNOrInfinity() OrElse playerProjectileUpdate.curVelocity.IsNaNOrInfinity() OrElse Single.IsNaN(playerProjectileUpdate.travelTime) OrElse Single.IsInfinity(playerProjectileUpdate.travelTime) Then
			Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, "Contains NaN (" + playerProjectileUpdate.projectileID.ToString() + ")", True)
			playerProjectileUpdate.ResetToPool()
			Return
		End If
		Dim firedProjectile As Global.BasePlayer.FiredProjectile
		If Not Me.firedProjectiles.TryGetValue(playerProjectileUpdate.projectileID, firedProjectile) Then
			Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, "Missing ID (" + playerProjectileUpdate.projectileID.ToString() + ")", False)
			playerProjectileUpdate.ResetToPool()
			Return
		End If
		If firedProjectile.firedTime < UnityEngine.Time.realtimeSinceStartup - 8F Then
			Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, "Lifetime is zero (" + playerProjectileUpdate.projectileID.ToString() + ")", True)
			Analytics.Azure.OnProjectileHackViolation(firedProjectile)
			playerProjectileUpdate.ResetToPool()
			Return
		End If
		If firedProjectile.ricochets > 0 Then
			Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, "Projectile is ricochet (" + playerProjectileUpdate.projectileID.ToString() + ")", True)
			Analytics.Azure.OnProjectileHackViolation(firedProjectile)
			playerProjectileUpdate.ResetToPool()
			Return
		End If
		Dim position As Vector3 = firedProjectile.position
		Dim positionOffset As Vector3 = firedProjectile.positionOffset
		Dim velocity As Vector3 = firedProjectile.velocity
		Dim num As Single = firedProjectile.trajectoryMismatch
		Dim partialTime As Single = firedProjectile.partialTime
		Dim travelTime As Single = firedProjectile.travelTime
		Dim num2 As Single = Mathf.Clamp(playerProjectileUpdate.travelTime, firedProjectile.travelTime, 8F)
		Dim vector As Vector3 = UnityEngine.Physics.gravity * firedProjectile.projectilePrefab.gravityModifier
		Dim drag As Single = firedProjectile.projectilePrefab.drag
		If firedProjectile.protection > 0 Then
			Dim num3 As Single = 1F - ConVar.AntiHack.projectile_forgiveness
			Dim num4 As Single = 1F + ConVar.AntiHack.projectile_forgiveness
			Dim projectile_clientframes As Single = ConVar.AntiHack.projectile_clientframes
			Dim projectile_serverframes As Single = ConVar.AntiHack.projectile_serverframes
			Dim num5 As Single = Mathx.Decrement(firedProjectile.firedTime)
			Dim num6 As Single = Mathf.Clamp(Mathx.Increment(UnityEngine.Time.realtimeSinceStartup) - num5, 0F, 8F)
			Dim num7 As Single = num2
			Dim num8 As Single = Mathf.Abs(num6 - num7)
			firedProjectile.desyncLifeTime = num8
			Dim num9 As Single = Mathf.Min(num6, num7)
			Dim num10 As Single = projectile_clientframes / 60F
			Dim num11 As Single = projectile_serverframes * Mathx.Max(UnityEngine.Time.deltaTime, UnityEngine.Time.smoothDeltaTime, UnityEngine.Time.fixedDeltaTime)
			Dim num12 As Single = (num9 + Me.desyncTimeClamped + num10 + num11) * num4
			Dim num13 As Single = Mathf.Max(0F, (num9 - Me.desyncTimeClamped - num10 - num11) * num3)
			Dim num14 As Integer = 1075904512
			If ConVar.AntiHack.projectile_terraincheck Then
				num14 = num14 Or 8388608
			End If
			If ConVar.AntiHack.projectile_vehiclecheck Then
				num14 = num14 Or 134217728
			End If
			If firedProjectile.protection >= 1 Then
				Dim num15 As Single = firedProjectile.projectilePrefab.initialDistance + num12 * firedProjectile.initialVelocity.magnitude
				Dim num16 As Single = Vector3.Distance(firedProjectile.initialPosition, playerProjectileUpdate.curPosition)
				If num16 > num15 Then
					Dim name As String = firedProjectile.projectilePrefab.name
					Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, String.Concat(New String() { "Projectile distance (", name, " with ", num16.ToString(), "m > ", num15.ToString(), "m in ", num12.ToString(), "s)" }), True)
					Analytics.Azure.OnProjectileHackViolation(firedProjectile)
					playerProjectileUpdate.ResetToPool()
					Return
				End If
				If num8 > ConVar.AntiHack.projectile_desync Then
					Dim name2 As String = firedProjectile.projectilePrefab.name
					Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, String.Concat(New String() { "Projectile desync (", name2, " with ", num8.ToString(), "s > ", ConVar.AntiHack.projectile_desync.ToString(), "s)" }), True)
					Analytics.Azure.OnProjectileHackViolation(firedProjectile)
					playerProjectileUpdate.ResetToPool()
					Return
				End If
				Dim curVelocity As Vector3 = playerProjectileUpdate.curVelocity
				Dim vector2 As Vector3 = firedProjectile.initialVelocity
				Dim a As Vector3 = If((firedProjectile.hits = 0), vector2, firedProjectile.velocity)
				Dim d As Single = drag * 0.03125F
				Dim b As Vector3 = vector * 0.03125F
				Dim num17 As Integer = Mathf.FloorToInt(num13 / 0.03125F)
				Dim num18 As Integer = Mathf.CeilToInt(num12 / 0.03125F)
				For i As Integer = 0 To num17 - 1
					vector2 += b
					vector2 -= vector2 * d
					a += b
					a -= a * d
				Next
				Dim magnitude As Single = curVelocity.magnitude
				Dim num19 As Single = vector2.magnitude
				Dim num20 As Single = a.magnitude
				For j As Integer = num17 To num18 - 1
					vector2 += b
					vector2 -= vector2 * d
					a += b
					a -= a * d
				Next
				num20 = Mathf.Min(num20, a.magnitude)
				num19 = Mathf.Max(num19, vector2.magnitude)
				If magnitude < num20 * num3 Then
					Dim name3 As String = firedProjectile.projectilePrefab.name
					Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, String.Concat(New String() { "Projectile velocity too low (", name3, " with ", magnitude.ToString(), " < ", num20.ToString(), ")" }), True)
					Analytics.Azure.OnProjectileHackViolation(firedProjectile)
					playerProjectileUpdate.ResetToPool()
					Return
				End If
				If magnitude > num19 * num4 Then
					Dim name4 As String = firedProjectile.projectilePrefab.name
					Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, String.Concat(New String() { "Projectile velocity too high (", name4, " with ", magnitude.ToString(), " > ", num19.ToString(), ")" }), True)
					Analytics.Azure.OnProjectileHackViolation(firedProjectile)
					playerProjectileUpdate.ResetToPool()
					Return
				End If
			End If
			If firedProjectile.protection >= 3 Then
				Dim position2 As Vector3 = firedProjectile.position
				Dim curPosition As Vector3 = playerProjectileUpdate.curPosition
				Dim b2 As Vector3 = Vector3.zero
				If ConVar.AntiHack.projectile_backtracking > 0F Then
					b2 = (curPosition - position2).normalized * ConVar.AntiHack.projectile_backtracking
				End If
				If Not GamePhysics.LineOfSight(position2 - b2, curPosition + b2, num14, firedProjectile.lastEntityHit) Then
					Dim name5 As String = firedProjectile.projectilePrefab.name
					Dim type As AntiHackType = AntiHackType.ProjectileHack
					Dim array As String() = New String(5) {}
					array(0) = "Line of sight ("
					array(1) = name5
					array(2) = " on update) "
					Dim num21 As Integer = 3
					Dim vector3 As Vector3 = position2
					array(num21) = vector3.ToString()
					array(4) = " "
					Dim num22 As Integer = 5
					vector3 = curPosition
					array(num22) = vector3.ToString()
					Global.AntiHack.Log(Me, type, String.Concat(array), True)
					Analytics.Azure.OnProjectileHackViolation(firedProjectile)
					playerProjectileUpdate.ResetToPool()
					Return
				End If
			End If
			If firedProjectile.protection >= 4 Then
				Dim a2 As Vector3
				Dim b3 As Vector3
				Me.SimulateProjectile(position, velocity, partialTime, num2 - travelTime, vector, drag, a2, b3)
				firedProjectile.simulatedPositions.Add(position)
				Dim line As Line = New Line(a2 - b3, position + b3)
				num += Mathf.Max(line.Distance(playerProjectileUpdate.curPosition) - positionOffset.magnitude, 0F)
			End If
			If firedProjectile.protection >= 5 Then
				If firedProjectile.inheritedVelocity <> Vector3.zero Then
					Dim curVelocity2 As Vector3 = firedProjectile.inheritedVelocity + velocity
					Dim curVelocity3 As Vector3 = playerProjectileUpdate.curVelocity
					If curVelocity3.magnitude > 2F * curVelocity2.magnitude OrElse curVelocity3.magnitude < 0.5F * curVelocity2.magnitude Then
						playerProjectileUpdate.curVelocity = curVelocity2
					End If
					firedProjectile.inheritedVelocity = Vector3.zero
				Else
					playerProjectileUpdate.curVelocity = velocity
				End If
			End If
		End If
		firedProjectile.updates.Add(New Global.BasePlayer.FiredProjectileUpdate() With { .OldPosition = firedProjectile.position, .NewPosition = playerProjectileUpdate.curPosition, .OldVelocity = firedProjectile.velocity, .NewVelocity = playerProjectileUpdate.curVelocity, .Mismatch = num, .PartialTime = partialTime })
		firedProjectile.position = playerProjectileUpdate.curPosition
		firedProjectile.velocity = playerProjectileUpdate.curVelocity
		firedProjectile.travelTime = playerProjectileUpdate.travelTime
		firedProjectile.partialTime = partialTime
		firedProjectile.trajectoryMismatch = num
		firedProjectile.positionOffset = Nothing
		Me.firedProjectiles(playerProjectileUpdate.projectileID) = firedProjectile
		playerProjectileUpdate.ResetToPool()
	End Sub

	' Token: 0x060006AA RID: 1706 RVA: 0x00050AB8 File Offset: 0x0004ECB8
	Private Sub SimulateProjectile(ByRef position As Vector3, ByRef velocity As Vector3, ByRef partialTime As Single, travelTime As Single, gravity As Vector3, drag As Single, <System.Runtime.InteropServices.OutAttribute()> ByRef prevPosition As Vector3, <System.Runtime.InteropServices.OutAttribute()> ByRef prevVelocity As Vector3)
		Dim num As Single = 0.03125F
		prevPosition = position
		prevVelocity = velocity
		If partialTime > Mathf.Epsilon Then
			Dim num2 As Single = num - partialTime
			If travelTime < num2 Then
				prevPosition = position
				prevVelocity = velocity
				position += velocity * travelTime
				partialTime += travelTime
				Return
			End If
			prevPosition = position
			prevVelocity = velocity
			position += velocity * num2
			velocity += gravity * num
			velocity -= velocity * (drag * num)
			travelTime -= num2
		End If
		Dim num3 As Integer = Mathf.FloorToInt(travelTime / num)
		For i As Integer = 0 To num3 - 1
			prevPosition = position
			prevVelocity = velocity
			position += velocity * num
			velocity += gravity * num
			velocity -= velocity * (drag * num)
		Next
		partialTime = travelTime - num * CSng(num3)
		If partialTime > Mathf.Epsilon Then
			prevPosition = position
			prevVelocity = velocity
			position += velocity * partialTime
		End If
	End Sub

	' Token: 0x060006AB RID: 1707 RVA: 0x00050C84 File Offset: 0x0004EE84
	Protected Overridable Sub CreateWorldProjectile(info As HitInfo, itemDef As ItemDefinition, itemMod As ItemModProjectile, projectilePrefab As Projectile, recycleItem As Global.Item)
		Dim projectileVelocity As Vector3 = info.ProjectileVelocity
		Dim item As Global.Item = If((recycleItem IsNot Nothing), recycleItem, ItemManager.Create(itemDef, 1, 0UL))
		Dim baseEntity As Global.BaseEntity
		If Not info.DidHit Then
			baseEntity = item.CreateWorldObject(info.HitPositionWorld, Quaternion.LookRotation(projectileVelocity.normalized), Nothing, 0UI)
			baseEntity.Kill(Global.BaseNetworkable.DestroyMode.Gib)
			Return
		End If
		If projectilePrefab.breakProbability > 0F AndAlso UnityEngine.Random.value <= projectilePrefab.breakProbability Then
			baseEntity = item.CreateWorldObject(info.HitPositionWorld, Quaternion.LookRotation(projectileVelocity.normalized), Nothing, 0UI)
			baseEntity.Kill(Global.BaseNetworkable.DestroyMode.Gib)
			Return
		End If
		If projectilePrefab.conditionLoss > 0F Then
			item.LoseCondition(projectilePrefab.conditionLoss * 100F)
			If item.isBroken Then
				baseEntity = item.CreateWorldObject(info.HitPositionWorld, Quaternion.LookRotation(projectileVelocity.normalized), Nothing, 0UI)
				baseEntity.Kill(Global.BaseNetworkable.DestroyMode.Gib)
				Return
			End If
		End If
		If projectilePrefab.stickProbability <= 0F OrElse UnityEngine.Random.value > projectilePrefab.stickProbability Then
			baseEntity = item.CreateWorldObject(info.HitPositionWorld, Quaternion.LookRotation(projectileVelocity.normalized), Nothing, 0UI)
			Dim component As Rigidbody = baseEntity.GetComponent(Of Rigidbody)()
			component.AddForce(projectileVelocity.normalized * 200F)
			component.WakeUp()
			Return
		End If
		If info.HitEntity Is Nothing Then
			baseEntity = item.CreateWorldObject(info.HitPositionWorld, Quaternion.LookRotation(projectileVelocity.normalized), Nothing, 0UI)
		ElseIf info.HitBone = 0UI Then
			baseEntity = item.CreateWorldObject(info.HitPositionLocal, Quaternion.LookRotation(info.HitEntity.transform.InverseTransformDirection(projectileVelocity.normalized)), info.HitEntity, 0UI)
		Else
			baseEntity = item.CreateWorldObject(info.HitPositionLocal, Quaternion.LookRotation(info.HitNormalLocal * -1F), info.HitEntity, info.HitBone)
		End If
		Dim droppedItem As DroppedItem = TryCast(baseEntity, DroppedItem)
		If droppedItem IsNot Nothing Then
			droppedItem.StickIn()
			Return
		End If
		baseEntity.GetComponent(Of Rigidbody)().isKinematic = True
	End Sub

	' Token: 0x060006AC RID: 1708 RVA: 0x00050E78 File Offset: 0x0004F078
	Public Sub CleanupExpiredProjectiles()
		Dim source As IEnumerable(Of KeyValuePair(Of Integer, Global.BasePlayer.FiredProjectile)) = Me.firedProjectiles
		Dim <>9__319_ As Func(Of KeyValuePair(Of Integer, Global.BasePlayer.FiredProjectile), Boolean) = Global.BasePlayer.<>c.<>9__319_0
		Dim predicate As Func(Of KeyValuePair(Of Integer, Global.BasePlayer.FiredProjectile), Boolean) = <>9__319_
		If <>9__319_ Is Nothing Then
			Dim func As Func(Of KeyValuePair(Of Integer, Global.BasePlayer.FiredProjectile), Boolean) = Function(x As KeyValuePair(Of Integer, Global.BasePlayer.FiredProjectile)) x.Value.firedTime < UnityEngine.Time.realtimeSinceStartup - 8F - 1F
			predicate = func
			Global.BasePlayer.<>c.<>9__319_0 = func
		End If
		For Each keyValuePair As KeyValuePair(Of Integer, Global.BasePlayer.FiredProjectile) In source.Where(predicate).ToList()
			Analytics.Azure.OnFiredProjectileRemoved(Me, keyValuePair.Value)
			Me.firedProjectiles.Remove(keyValuePair.Key)
			Dim value As Global.BasePlayer.FiredProjectile = keyValuePair.Value
			Facepunch.Pool.Free(Of Global.BasePlayer.FiredProjectile)(value)
		Next
	End Sub

	' Token: 0x060006AD RID: 1709 RVA: 0x00050F1C File Offset: 0x0004F11C
	Public Function HasFiredProjectile(id As Integer) As Boolean
		Return Me.firedProjectiles.ContainsKey(id)
	End Function

	' Token: 0x060006AE RID: 1710 RVA: 0x00050F2C File Offset: 0x0004F12C
	Public Sub NoteFiredProjectile(projectileid As Integer, startPos As Vector3, startVel As Vector3, attackEnt As AttackEntity, firedItemDef As ItemDefinition, projectileGroupId As Guid, positionOffset As Vector3, Optional pickupItem As Global.Item = Nothing)
		Dim baseProjectile As Global.BaseProjectile = TryCast(attackEnt, Global.BaseProjectile)
		Dim component As ItemModProjectile = firedItemDef.GetComponent(Of ItemModProjectile)()
		Dim component2 As Projectile = component.projectileObject.[Get]().GetComponent(Of Projectile)()
		If startPos.IsNaNOrInfinity() OrElse startVel.IsNaNOrInfinity() Then
			Dim name As String = component2.name
			Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, "Contains NaN (" + name + ")", True)
			Me.stats.combat.LogInvalid(Me, baseProjectile, "projectile_nan")
			Return
		End If
		Dim projectile_protection As Integer = ConVar.AntiHack.projectile_protection
		Dim inheritedVelocity As Vector3 = If((attackEnt IsNot Nothing), attackEnt.GetInheritedVelocity(Me, startVel.normalized), Vector3.zero)
		If projectile_protection >= 1 Then
			Dim num As Single = 1F - ConVar.AntiHack.projectile_forgiveness
			Dim num2 As Single = 1F + ConVar.AntiHack.projectile_forgiveness
			Dim magnitude As Single = startVel.magnitude
			Dim num3 As Single = component.GetMinVelocity()
			Dim num4 As Single = component.GetMaxVelocity()
			Dim baseProjectile2 As Global.BaseProjectile = TryCast(attackEnt, Global.BaseProjectile)
			If baseProjectile2 Then
				num3 *= baseProjectile2.GetProjectileVelocityScale(False)
				num4 *= baseProjectile2.GetProjectileVelocityScale(True)
			End If
			num3 *= num
			num4 *= num2
			If magnitude < num3 Then
				Dim name2 As String = component2.name
				Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, String.Concat(New String() { "Velocity (", name2, " with ", magnitude.ToString(), " < ", num3.ToString(), ")" }), True)
				Me.stats.combat.LogInvalid(Me, baseProjectile, "projectile_minvelocity")
				Return
			End If
			If magnitude > num4 Then
				Dim name3 As String = component2.name
				Global.AntiHack.Log(Me, AntiHackType.ProjectileHack, String.Concat(New String() { "Velocity (", name3, " with ", magnitude.ToString(), " > ", num4.ToString(), ")" }), True)
				Me.stats.combat.LogInvalid(Me, baseProjectile, "projectile_maxvelocity")
				Return
			End If
		End If
		Dim firedProjectile As Global.BasePlayer.FiredProjectile = Facepunch.Pool.[Get](Of Global.BasePlayer.FiredProjectile)()
		firedProjectile.itemDef = firedItemDef
		firedProjectile.itemMod = component
		firedProjectile.projectilePrefab = component2
		firedProjectile.firedTime = UnityEngine.Time.realtimeSinceStartup
		firedProjectile.travelTime = 0F
		firedProjectile.weaponSource = attackEnt
		firedProjectile.weaponPrefab = If((attackEnt Is Nothing), Nothing, GameManager.server.FindPrefab(StringPool.[Get](attackEnt.prefabID)).GetComponent(Of AttackEntity)())
		firedProjectile.projectileModifier = If((baseProjectile Is Nothing), Projectile.Modifier.[Default], baseProjectile.GetProjectileModifier())
		firedProjectile.pickupItem = pickupItem
		firedProjectile.integrity = 1F
		firedProjectile.position = startPos
		firedProjectile.initialPositionOffset = positionOffset
		firedProjectile.positionOffset = positionOffset
		firedProjectile.velocity = startVel
		firedProjectile.initialPosition = startPos
		firedProjectile.initialVelocity = startVel
		firedProjectile.inheritedVelocity = inheritedVelocity
		firedProjectile.protection = projectile_protection
		firedProjectile.ricochets = 0
		firedProjectile.hits = 0
		firedProjectile.id = projectileid
		firedProjectile.attacker = Me
		Me.firedProjectiles.Add(projectileid, firedProjectile)
		Analytics.Azure.OnFiredProjectile(Me, firedProjectile, projectileGroupId)
	End Sub

	' Token: 0x060006AF RID: 1711 RVA: 0x00051240 File Offset: 0x0004F440
	Public Sub ServerNoteFiredProjectile(projectileid As Integer, startPos As Vector3, startVel As Vector3, attackEnt As AttackEntity, firedItemDef As ItemDefinition, Optional pickupItem As Global.Item = Nothing)
		Dim baseProjectile As Global.BaseProjectile = TryCast(attackEnt, Global.BaseProjectile)
		Dim component As ItemModProjectile = firedItemDef.GetComponent(Of ItemModProjectile)()
		Dim component2 As Projectile = component.projectileObject.[Get]().GetComponent(Of Projectile)()
		Dim protection As Integer = 0
		Dim zero As Vector3 = Vector3.zero
		If startPos.IsNaNOrInfinity() OrElse startVel.IsNaNOrInfinity() Then
			Return
		End If
		Dim firedProjectile As Global.BasePlayer.FiredProjectile = Facepunch.Pool.[Get](Of Global.BasePlayer.FiredProjectile)()
		firedProjectile.itemDef = firedItemDef
		firedProjectile.itemMod = component
		firedProjectile.projectilePrefab = component2
		firedProjectile.firedTime = UnityEngine.Time.realtimeSinceStartup
		firedProjectile.travelTime = 0F
		firedProjectile.weaponSource = attackEnt
		firedProjectile.weaponPrefab = If((attackEnt Is Nothing), Nothing, GameManager.server.FindPrefab(StringPool.[Get](attackEnt.prefabID)).GetComponent(Of AttackEntity)())
		firedProjectile.projectileModifier = If((baseProjectile Is Nothing), Projectile.Modifier.[Default], baseProjectile.GetProjectileModifier())
		firedProjectile.pickupItem = pickupItem
		firedProjectile.integrity = 1F
		firedProjectile.trajectoryMismatch = 0F
		firedProjectile.position = startPos
		firedProjectile.positionOffset = Vector3.zero
		firedProjectile.velocity = startVel
		firedProjectile.initialPosition = startPos
		firedProjectile.initialVelocity = startVel
		firedProjectile.inheritedVelocity = zero
		firedProjectile.protection = protection
		firedProjectile.ricochets = 0
		firedProjectile.hits = 0
		firedProjectile.id = projectileid
		firedProjectile.attacker = Me
		firedProjectile.simulatedPositions.Add(startPos)
		Me.firedProjectiles.Add(projectileid, firedProjectile)
	End Sub

	' Token: 0x060006B0 RID: 1712 RVA: 0x000513AE File Offset: 0x0004F5AE
	Public Overrides Function CanUseNetworkCache(connection As Network.Connection) As Boolean
		Return Me.net Is Nothing OrElse (connection.authLevel <= 0UI AndAlso Me.net.connection IsNot connection)
	End Function

	' Token: 0x060006B1 RID: 1713 RVA: 0x000513D6 File Offset: 0x0004F5D6
	Public Overrides Sub PostServerLoad()
		MyBase.PostServerLoad()
		Me.HandleMountedOnLoad()
	End Sub

	' Token: 0x060006B2 RID: 1714 RVA: 0x000513E4 File Offset: 0x0004F5E4
	Public Overrides Sub Save(info As Global.BaseNetworkable.SaveInfo)
		MyBase.Save(info)
		Dim flag As Boolean = Me.net IsNot Nothing AndAlso Me.net.connection Is info.forConnection
		Dim flag2 As Boolean
		If Not info.forDisk AndAlso info.forConnection.player IsNot Nothing Then
			Dim basePlayer As Global.BasePlayer = TryCast(info.forConnection.player, Global.BasePlayer)
			If basePlayer IsNot Nothing Then
				flag2 = basePlayer.IsAdmin
				GoTo IL_5E
			End If
		End If
		flag2 = False
		IL_5E:
		Dim flag3 As Boolean = flag2
		info.msg.basePlayer = Facepunch.Pool.[Get](Of ProtoBuf.BasePlayer)()
		info.msg.basePlayer.userid = Me.userID
		info.msg.basePlayer.name = Me.displayName
		info.msg.basePlayer.playerFlags = CInt(Me.playerFlags)
		info.msg.basePlayer.currentTeam = Me.currentTeam
		info.msg.basePlayer.heldEntity = Me.svActiveItemID
		info.msg.basePlayer.reputation = Me.reputation
		If Not info.forDisk AndAlso Me.currentGesture IsNot Nothing AndAlso Me.currentGesture.animationType = GestureConfig.AnimationType.[Loop] Then
			info.msg.basePlayer.loopingGesture = Me.currentGesture.gestureId
		End If
		If Me.IsConnected AndAlso (Me.IsAdmin OrElse Me.IsDeveloper) Then
			info.msg.basePlayer.skinCol = Me.net.connection.info.GetFloat("global.skincol", -1F)
			info.msg.basePlayer.skinTex = Me.net.connection.info.GetFloat("global.skintex", -1F)
			info.msg.basePlayer.skinMesh = Me.net.connection.info.GetFloat("global.skinmesh", -1F)
		Else
			info.msg.basePlayer.skinCol = -1F
			info.msg.basePlayer.skinTex = -1F
			info.msg.basePlayer.skinMesh = -1F
		End If
		info.msg.basePlayer.underwear = Me.GetUnderwearSkin()
		If info.forDisk OrElse flag Then
			info.msg.basePlayer.metabolism = Me.metabolism.Save()
			info.msg.basePlayer.modifiers = Nothing
			If Me.modifiers IsNot Nothing Then
				info.msg.basePlayer.modifiers = Me.modifiers.Save()
			End If
		End If
		If Not info.forDisk AndAlso Not flag Then
			info.msg.basePlayer.playerFlags = info.msg.basePlayer.playerFlags And -5
			info.msg.basePlayer.playerFlags = info.msg.basePlayer.playerFlags And -129
			If info.msg.baseCombat IsNot Nothing AndAlso Not flag3 Then
				info.msg.baseCombat.health = 100F
			End If
		End If
		info.msg.basePlayer.inventory = Me.inventory.Save(info.forDisk OrElse flag)
		Me.modelState.sleeping = Me.IsSleeping()
		Me.modelState.relaxed = Me.IsRelaxed()
		Me.modelState.crawling = Me.IsCrawling()
		Me.modelState.loading = Me.IsLoadingAfterTransfer()
		info.msg.basePlayer.modelState = Me.modelState.Copy()
		If info.forDisk Then
			Dim baseEntity As Global.BaseEntity = Me.mounted.[Get](MyBase.isServer)
			If baseEntity.IsValid() Then
				If baseEntity.enableSaving Then
					info.msg.basePlayer.mounted = Me.mounted.uid
				Else
					Dim mountedVehicle As Global.BaseVehicle = Me.GetMountedVehicle()
					If mountedVehicle.IsValid() AndAlso mountedVehicle.enableSaving Then
						info.msg.basePlayer.mounted = mountedVehicle.net.ID
					End If
				End If
			End If
			info.msg.basePlayer.respawnId = Me.respawnId
		Else
			info.msg.basePlayer.mounted = Me.mounted.uid
		End If
		If flag Then
			info.msg.basePlayer.persistantData = Me.PersistantPlayerInfo.Copy()
			If Not info.forDisk AndAlso Me.State.missions IsNot Nothing Then
				info.msg.basePlayer.missions = Me.State.missions.Copy()
			End If
		End If
		info.msg.basePlayer.bagCount = Global.SleepingBag.GetSleepingBagCount(Me.userID)
		info.msg.basePlayer.shelterCount = Global.LegacyShelter.GetShelterCount(Me.userID)
		If info.forDisk Then
			info.msg.basePlayer.loadingTimeout = Me.timeUntilLoadingExpires
			info.msg.basePlayer.currentLife = Me.lifeStory
			info.msg.basePlayer.previousLife = Me.previousLifeStory
		End If
		If Not info.forDisk Then
			info.msg.basePlayer.clanId = Me.clanId
		End If
		If info.forDisk Then
			info.msg.basePlayer.itemCrafter = Me.inventory.crafting.Save()
		End If
		If info.forDisk Then
			Me.SavePlayerState()
		End If
		info.msg.basePlayer.tutorialAllowance = CInt(Me.CurrentTutorialAllowance)
	End Sub

	' Token: 0x060006B3 RID: 1715 RVA: 0x00051970 File Offset: 0x0004FB70
	Public Overrides Sub Load(info As Global.BaseNetworkable.LoadInfo)
		MyBase.Load(info)
		If info.msg.basePlayer IsNot Nothing Then
			Dim basePlayer As ProtoBuf.BasePlayer = info.msg.basePlayer
			Me.userID = basePlayer.userid
			Me.UserIDString = Me.userID.ToString()
			If basePlayer.name IsNot Nothing Then
				Me.displayName = basePlayer.name
			End If
			Dim playerFlags As Global.BasePlayer.PlayerFlags = Me.playerFlags
			Me.playerFlags = CType(basePlayer.playerFlags, Global.BasePlayer.PlayerFlags)
			Me.currentTeam = basePlayer.currentTeam
			Me.reputation = basePlayer.reputation
			If basePlayer.metabolism IsNot Nothing Then
				Me.metabolism.Load(basePlayer.metabolism)
			End If
			If basePlayer.modifiers IsNot Nothing AndAlso Me.modifiers IsNot Nothing Then
				Me.modifiers.Load(basePlayer.modifiers)
			End If
			If basePlayer.inventory IsNot Nothing Then
				Me.inventory.Load(basePlayer.inventory)
			End If
			If basePlayer.modelState IsNot Nothing Then
				If Me.modelState IsNot Nothing Then
					Me.modelState.ResetToPool()
					Me.modelState = Nothing
				End If
				Me.modelState = basePlayer.modelState
				basePlayer.modelState = Nothing
			End If
			If info.fromDisk Then
				Me.timeUntilLoadingExpires = info.msg.basePlayer.loadingTimeout
				If Me.timeUntilLoadingExpires > 0F Then
					Dim time As Single = Mathf.Clamp(Me.timeUntilLoadingExpires, 0F, Nexus.loadingTimeout)
					MyBase.Invoke(AddressOf Me.RemoveLoadingPlayerFlag, time)
				End If
				Me.lifeStory = info.msg.basePlayer.currentLife
				If Me.lifeStory IsNot Nothing Then
					Me.lifeStory.ShouldPool = False
				End If
				Me.previousLifeStory = info.msg.basePlayer.previousLife
				If Me.previousLifeStory IsNot Nothing Then
					Me.previousLifeStory.ShouldPool = False
				End If
				Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.Sleeping, False)
				Me.StartSleeping()
				Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.Connected, False)
				If Me.lifeStory Is Nothing AndAlso Me.IsAlive() Then
					Me.LifeStoryStart()
				End If
				Me.mounted.uid = info.msg.basePlayer.mounted
				If Me.IsWounded() Then
					Me.Die(Nothing)
				End If
				Me.respawnId = info.msg.basePlayer.respawnId
				Dim itemCrafter As ProtoBuf.ItemCrafter = info.msg.basePlayer.itemCrafter
				If If((itemCrafter IsNot Nothing), itemCrafter.queue, Nothing) IsNot Nothing Then
					Me.inventory.crafting.Load(info.msg.basePlayer.itemCrafter)
				End If
			End If
			If Not info.fromDisk Then
				Me.clanId = info.msg.basePlayer.clanId
			End If
			Me.CurrentTutorialAllowance = CType(info.msg.basePlayer.tutorialAllowance, Global.BasePlayer.TutorialItemAllowance)
		End If
	End Sub

	' Token: 0x170000C4 RID: 196
	' (get) Token: 0x060006B4 RID: 1716 RVA: 0x00051C32 File Offset: 0x0004FE32
	Public Overridable ReadOnly Property Family As BaseNpc.AiStatistics.FamilyEnum
		Get
			Return BaseNpc.AiStatistics.FamilyEnum.Player
		End Get
	End Property

	' Token: 0x170000C5 RID: 197
	' (get) Token: 0x060006B5 RID: 1717 RVA: 0x00051C36 File Offset: 0x0004FE36
	Protected Overrides ReadOnly Property PositionTickRate As Single
		Get
			Return -1F
		End Get
	End Property

	' Token: 0x170000C6 RID: 198
	' (get) Token: 0x060006B6 RID: 1718 RVA: 0x00051C3D File Offset: 0x0004FE3D
	' (set) Token: 0x060006B7 RID: 1719 RVA: 0x00051C45 File Offset: 0x0004FE45
	Public Property DebugMapMarkerIndex As Integer

	' Token: 0x170000C7 RID: 199
	' (get) Token: 0x060006B8 RID: 1720 RVA: 0x00051C4E File Offset: 0x0004FE4E
	' (set) Token: 0x060006B9 RID: 1721 RVA: 0x00051C56 File Offset: 0x0004FE56
	Public Property LastBlockColourChangeId As UInteger

	' Token: 0x170000C8 RID: 200
	' (get) Token: 0x060006BA RID: 1722 RVA: 0x00051C5F File Offset: 0x0004FE5F
	' (set) Token: 0x060006BB RID: 1723 RVA: 0x00051C67 File Offset: 0x0004FE67
	Public Property PlayHeavyLandingAnimation As Boolean

	' Token: 0x170000C9 RID: 201
	' (get) Token: 0x060006BC RID: 1724 RVA: 0x00051C70 File Offset: 0x0004FE70
	Public ReadOnly Property Chunk As ServerOcclusion.Grid
		Get
			Return ServerOcclusion.GetGrid(Me.eyes.position)
		End Get
	End Property

	' Token: 0x170000CA RID: 202
	' (get) Token: 0x060006BD RID: 1725 RVA: 0x00051C82 File Offset: 0x0004FE82
	Public ReadOnly Property SubGrid As ServerOcclusion.SubGrid
		Get
			Return ServerOcclusion.GetSubGrid(Me.eyes.position)
		End Get
	End Property

	' Token: 0x170000CB RID: 203
	' (get) Token: 0x060006BE RID: 1726 RVA: 0x00051C94 File Offset: 0x0004FE94
	Public ReadOnly Property EstimatedSubGrid As ServerOcclusion.SubGrid
		Get
			Return ServerOcclusion.GetSubGrid(Me.eyes.position + Me.estimatedVelocityClamped)
		End Get
	End Property

	' Token: 0x060006BF RID: 1727 RVA: 0x00051CB1 File Offset: 0x0004FEB1
	Friend Overrides Sub OnParentRemoved()
		If Me.IsNpc Then
			MyBase.OnParentRemoved()
			Return
		End If
		MyBase.SetParent(Nothing, True, True)
	End Sub

	' Token: 0x060006C0 RID: 1728 RVA: 0x00051CCB File Offset: 0x0004FECB
	Public Overrides Sub OnParentChanging(oldParent As Global.BaseEntity, newParent As Global.BaseEntity)
		If oldParent IsNot Nothing Then
			Me.TransformState(oldParent.transform.localToWorldMatrix)
		End If
		If newParent IsNot Nothing Then
			Me.TransformState(newParent.transform.worldToLocalMatrix)
		End If
	End Sub

	' Token: 0x060006C1 RID: 1729 RVA: 0x00051D04 File Offset: 0x0004FF04
	Private Sub TransformState(matrix As Matrix4x4)
		Me.tickInterpolator.TransformEntries(matrix)
		Me.tickHistory.TransformEntries(matrix)
		Dim euler As Vector3 = New Vector3(0F, matrix.rotation.eulerAngles.y, 0F)
		Me.eyes.bodyRotation = Quaternion.Euler(euler) * Me.eyes.bodyRotation
	End Sub

	' Token: 0x060006C2 RID: 1730 RVA: 0x00051D6F File Offset: 0x0004FF6F
	Public Function CanSuicide() As Boolean
		Return Me.IsAdmin OrElse Me.IsDeveloper OrElse UnityEngine.Time.realtimeSinceStartup > Me.nextSuicideTime
	End Function

	' Token: 0x060006C3 RID: 1731 RVA: 0x00051D90 File Offset: 0x0004FF90
	Public Sub MarkSuicide()
		Me.nextSuicideTime = UnityEngine.Time.realtimeSinceStartup + 60F
	End Sub

	' Token: 0x060006C4 RID: 1732 RVA: 0x00051DA3 File Offset: 0x0004FFA3
	Public Function CanRespawn() As Boolean
		Return UnityEngine.Time.realtimeSinceStartup > Me.nextRespawnTime
	End Function

	' Token: 0x060006C5 RID: 1733 RVA: 0x00051DB2 File Offset: 0x0004FFB2
	Public Sub MarkRespawn(Optional nextSpawnDelay As Single = 5F)
		Me.nextRespawnTime = UnityEngine.Time.realtimeSinceStartup + nextSpawnDelay
	End Sub

	' Token: 0x060006C6 RID: 1734 RVA: 0x00051DC4 File Offset: 0x0004FFC4
	Public Function GetActiveItem() As Global.Item
		If Not Me.svActiveItemID.IsValid Then
			Return Nothing
		End If
		If Me.IsDead() Then
			Return Nothing
		End If
		If Me.inventory Is Nothing OrElse Me.inventory.containerBelt Is Nothing Then
			Return Nothing
		End If
		Return Me.inventory.containerBelt.FindItemByUID(Me.svActiveItemID)
	End Function

	' Token: 0x060006C7 RID: 1735 RVA: 0x00051E20 File Offset: 0x00050020
	Public Sub MovePosition(newPos As Vector3)
		MyBase.transform.position = newPos
		If Me.parentEntity.[Get](MyBase.isServer) IsNot Nothing Then
			Me.tickInterpolator.Reset(Me.parentEntity.[Get](MyBase.isServer).transform.InverseTransformPoint(newPos))
		Else
			Me.tickInterpolator.Reset(newPos)
		End If
		Me.ticksPerSecond.Increment()
		Me.tickHistory.AddPoint(newPos, Me.tickHistoryCapacity)
		MyBase.NetworkPositionTick()
	End Sub

	' Token: 0x170000CC RID: 204
	' (get) Token: 0x060006C8 RID: 1736 RVA: 0x00051EAA File Offset: 0x000500AA
	' (set) Token: 0x060006C9 RID: 1737 RVA: 0x00051EB2 File Offset: 0x000500B2
	Public Property estimatedVelocity As Vector3

	' Token: 0x170000CD RID: 205
	' (get) Token: 0x060006CA RID: 1738 RVA: 0x00051EBB File Offset: 0x000500BB
	Public ReadOnly Property estimatedVelocityClamped As Vector3
		Get
			Return Vector3.ClampMagnitude(Me.estimatedVelocity, Me.GetMaxSpeed())
		End Get
	End Property

	' Token: 0x170000CE RID: 206
	' (get) Token: 0x060006CB RID: 1739 RVA: 0x00051ECE File Offset: 0x000500CE
	' (set) Token: 0x060006CC RID: 1740 RVA: 0x00051ED6 File Offset: 0x000500D6
	Public Property estimatedSpeed As Single

	' Token: 0x170000CF RID: 207
	' (get) Token: 0x060006CD RID: 1741 RVA: 0x00051EDF File Offset: 0x000500DF
	' (set) Token: 0x060006CE RID: 1742 RVA: 0x00051EE7 File Offset: 0x000500E7
	Public Property estimatedSpeed2D As Single

	' Token: 0x170000D0 RID: 208
	' (get) Token: 0x060006CF RID: 1743 RVA: 0x00051EF0 File Offset: 0x000500F0
	' (set) Token: 0x060006D0 RID: 1744 RVA: 0x00051EF8 File Offset: 0x000500F8
	Public Property secondsConnected As Integer

	' Token: 0x170000D1 RID: 209
	' (get) Token: 0x060006D1 RID: 1745 RVA: 0x00051F01 File Offset: 0x00050101
	' (set) Token: 0x060006D2 RID: 1746 RVA: 0x00051F09 File Offset: 0x00050109
	Public Property desyncTimeRaw As Single

	' Token: 0x170000D2 RID: 210
	' (get) Token: 0x060006D3 RID: 1747 RVA: 0x00051F12 File Offset: 0x00050112
	' (set) Token: 0x060006D4 RID: 1748 RVA: 0x00051F1A File Offset: 0x0005011A
	Public Property desyncTimeClamped As Single

	' Token: 0x060006D5 RID: 1749 RVA: 0x00051F23 File Offset: 0x00050123
	Public Sub OverrideViewAngles(newAng As Vector3)
		Me.viewAngles = newAng
	End Sub

	' Token: 0x060006D6 RID: 1750 RVA: 0x00051F2C File Offset: 0x0005012C
	Public Overrides Sub ServerInit()
		Me.stats = New PlayerStatistics(Me)
		If Me.userID = 0UL Then
			Me.userID = CULng(CLng(UnityEngine.Random.Range(0, 10000000)))
			Me.UserIDString = Me.userID.ToString()
			Me.displayName = Me.UserIDString
			Global.BasePlayer.bots.Add(Me)
		End If
		Me.EnablePlayerCollider()
		Me.SetPlayerRigidbodyState(Not Me.IsSleeping())
		MyBase.ServerInit()
		Me.eyes.bodyRotation = MyBase.transform.rotation
		Global.BaseEntity.Query.Server.AddPlayer(Me)
		Me.inventory.ServerInit(Me)
		Me.metabolism.ServerInit(Me)
		If Me.modifiers IsNot Nothing Then
			Me.modifiers.ServerInit(Me)
		End If
		If Me.recentWaveTargets IsNot Nothing Then
			Me.recentWaveTargets.Clear()
		End If
	End Sub

	' Token: 0x060006D7 RID: 1751 RVA: 0x00052018 File Offset: 0x00050218
	Friend Overrides Sub DoServerDestroy()
		MyBase.DoServerDestroy()
		Global.BaseEntity.Query.Server.RemovePlayer(Me)
		If Me.inventory Then
			Me.inventory.DoDestroy()
		End If
		Global.BasePlayer.sleepingPlayerList.Remove(Me)
		Me.SavePlayerState()
		If Me.cachedPersistantPlayer IsNot Nothing Then
			Facepunch.Pool.Free(Of PersistantPlayer)(Me.cachedPersistantPlayer)
		End If
	End Sub

	' Token: 0x060006D8 RID: 1752 RVA: 0x00052074 File Offset: 0x00050274
	Protected Sub ServerUpdate(deltaTime As Single)
		If Not Network.Net.sv.IsConnected() Then
			Return
		End If
		Me.LifeStoryUpdate(deltaTime, If(Me.IsOnGround(), Me.estimatedSpeed, 0F))
		Me.FinalizeTick(deltaTime)
		If ServerOcclusion.OcclusionEnabled Then
			Dim subscribers As List(Of Network.Connection) = MyBase.GetSubscribers()
			If subscribers IsNot Nothing AndAlso subscribers.Count > 0 Then
				For Each connection As Network.Connection In subscribers
					Dim basePlayer As Global.BasePlayer = TryCast(connection.player, Global.BasePlayer)
					If Not(basePlayer Is Nothing) Then
						Me.ShouldNetworkTo(basePlayer)
					End If
				Next
			End If
		End If
		Me.ThinkMissions(deltaTime)
		Me.desyncTimeRaw = Mathf.Max(Me.timeSinceLastTick - deltaTime, 0F)
		Me.desyncTimeClamped = Mathf.Min(Me.desyncTimeRaw, ConVar.AntiHack.maxdesync)
		If ConVar.AntiHack.terrain_protection > 0 AndAlso CLng((UnityEngine.Time.frameCount Mod ConVar.AntiHack.terrain_timeslice)) = CLng((CULng(CUInt(Me.net.ID.Value)) Mod CULng(CLng(ConVar.AntiHack.terrain_timeslice)))) AndAlso Not Global.AntiHack.ShouldIgnore(Me) Then
			Dim flag As Boolean = False
			If Global.AntiHack.IsInsideTerrain(Me) Then
				flag = True
				Global.AntiHack.AddViolation(Me, AntiHackType.InsideTerrain, ConVar.AntiHack.terrain_penalty)
			ElseIf ConVar.AntiHack.terrain_check_geometry AndAlso Global.AntiHack.IsInsideMesh(Me.eyes.position) Then
				flag = True
				Global.AntiHack.AddViolation(Me, AntiHackType.InsideGeometry, ConVar.AntiHack.terrain_penalty)
				Global.AntiHack.Log(Me, AntiHackType.InsideGeometry, "Seems to be clipped inside " + Global.AntiHack.isInsideRayHit.collider.name, True)
			End If
			If flag AndAlso ConVar.AntiHack.terrain_kill Then
				Analytics.Azure.OnTerrainHackViolation(Me)
				MyBase.Hurt(1000F, DamageType.Suicide, Me, False)
				Return
			End If
		End If
		Dim serverTickInterval As Single = Player.serverTickInterval
		If UnityEngine.Time.realtimeSinceStartup < Me.lastPlayerTick + serverTickInterval Then
			Return
		End If
		If Me.lastPlayerTick < UnityEngine.Time.realtimeSinceStartup - serverTickInterval * 100F Then
			Me.lastPlayerTick = UnityEngine.Time.realtimeSinceStartup - UnityEngine.Random.Range(0F, serverTickInterval)
		End If
		While Me.lastPlayerTick < UnityEngine.Time.realtimeSinceStartup
			Me.lastPlayerTick += serverTickInterval
		End While
		If Me.IsConnected Then
			Me.ConnectedPlayerUpdate(serverTickInterval)
		End If
		If Not Me.IsNpc Then
			Me.TickPings()
		End If
	End Sub

	' Token: 0x060006D9 RID: 1753 RVA: 0x0005229C File Offset: 0x0005049C
	Private Sub ServerUpdateBots(deltaTime As Single)
		Me.RefreshColliderSize(False)
	End Sub

	' Token: 0x060006DA RID: 1754 RVA: 0x000522A8 File Offset: 0x000504A8
	Private Sub ConnectedPlayerUpdate(deltaTime As Single)
		If Me.IsReceivingSnapshot Then
			Me.net.UpdateSubscriptions(Integer.MaxValue, Integer.MaxValue)
		ElseIf UnityEngine.Time.realtimeSinceStartup > Me.lastSubscriptionTick + ConVar.Server.entitybatchtime AndAlso Me.net.UpdateSubscriptions(ConVar.Server.entitybatchsize * 2, ConVar.Server.entitybatchsize) Then
			Me.lastSubscriptionTick = UnityEngine.Time.realtimeSinceStartup
		End If
		Me.SendEntityUpdate()
		If Me.IsReceivingSnapshot Then
			If Me.SnapshotQueue.Length = 0 AndAlso EACServer.IsAuthenticated(Me.net.connection) Then
				Me.EnterGame()
			End If
			Return
		End If
		If Me.IsAlive() Then
			Me.metabolism.ServerUpdate(Me, deltaTime)
			If Me.isMounted Then
				Me.PauseVehicleNoClipDetection(1F)
			End If
			If Me.modifiers IsNot Nothing AndAlso Not Me.IsReceivingSnapshot Then
				Me.modifiers.ServerUpdate(Me)
			End If
			If Me.InSafeZone() Then
				Dim num As Single = 0F
				Dim heldEntity As Global.HeldEntity = Me.GetHeldEntity()
				If heldEntity AndAlso heldEntity.hostile Then
					num = deltaTime
				End If
				If num = 0F Then
					Me.MarkWeaponDrawnDuration(0F)
				Else
					Me.AddWeaponDrawnDuration(num)
				End If
				If Me.weaponDrawnDuration >= 8F Then
					Me.MarkHostileFor(30F)
				End If
			Else
				Me.MarkWeaponDrawnDuration(0F)
			End If
			If Me.PlayHeavyLandingAnimation AndAlso Not Me.modelState.mounted AndAlso Me.modelState.onground AndAlso Parachute.LandingAnimations Then
				Me.Server_StartGesture(GestureCollection.HeavyLandingId)
				Me.PlayHeavyLandingAnimation = False
			End If
			If Me.timeSinceLastTick > CSng(ConVar.Server.playertimeout) Then
				Me.lastTickTime = 0F
				Me.Kick("Unresponsive")
				Return
			End If
		End If
		Dim num2 As Integer = CInt(Me.net.connection.GetSecondsConnected())
		Dim num3 As Integer = num2 - Me.secondsConnected
		If num3 > 0 Then
			Me.stats.Add("time", num3, Global.Stats.Server)
			Me.secondsConnected = num2
		End If
		If Me.IsLoadingAfterTransfer() Then
			Debug.LogWarning("Force removing loading flag for player (sanity check failed)", Me)
			Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.LoadingAfterTransfer, False)
		End If
		Me.RefreshColliderSize(False)
		Me.SendModelState(False)
	End Sub

	' Token: 0x060006DB RID: 1755 RVA: 0x000524BC File Offset: 0x000506BC
	Private Sub EnterGame()
		Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.ReceivingSnapshot, False)
		Dim flag As Boolean = False
		If Me.IsLoadingAfterTransfer() Then
			Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.LoadingAfterTransfer, False)
			Me.EndSleeping()
			flag = True
		End If
		If MyBase.IsTransferProtected() Then
			Dim vehicleParent As Global.BaseVehicle = Me.GetVehicleParent()
			If vehicleParent Is Nothing OrElse vehicleParent.ShouldDisableTransferProtectionOnLoad(Me) Then
				Me.DisableTransferProtection()
				flag = True
			End If
		End If
		If flag Then
			MyBase.SendNetworkUpdateImmediate(False)
		End If
		MyBase.ClientRPC(RpcTarget.Player("FinishLoading", Me))
		MyBase.Invoke(AddressOf Me.DelayedTeamUpdate, 1F)
		Me.LoadMissions(Me.State.missions)
		Me.MissionDirty(True)
		Dim num As Double = Me.State.unHostileTimestamp - TimeEx.currentTimestamp
		If num > 0.0 Then
			MyBase.ClientRPC(Of Single)(RpcTarget.Player("SetHostileLength", Me), CSng(num))
		End If
		If MyBase.IsTransferProtected() AndAlso MyBase.TransferProtectionRemaining > 0F Then
			MyBase.ClientRPC(Of Single)(RpcTarget.Player("SetTransferProtectionDuration", Me), MyBase.TransferProtectionRemaining)
		End If
		If Me.modifiers IsNot Nothing Then
			Me.modifiers.ResetTicking()
		End If
		If Me.net IsNot Nothing Then
			EACServer.OnFinishLoading(Me.net.connection)
		End If
		Debug.Log(String.Format("{0} has spawned", Me))
		If If((Demo.recordlistmode = 0), Demo.recordlist.Contains(Me.UserIDString), (Not Demo.recordlist.Contains(Me.UserIDString))) Then
			Me.StartDemoRecording()
		End If
		Me.SendClientPetLink()
		MyBase.ClientRPC(Of Vector3)(RpcTarget.Player("ForceViewAnglesTo", Me), MyBase.transform.forward)
		Me.HandleTutorialOnGameEnter()
	End Sub

	' Token: 0x060006DC RID: 1756 RVA: 0x0005265C File Offset: 0x0005085C
	Private Sub HandleTutorialOnGameEnter()
		If Global.TutorialIsland.ShouldPlayerResumeTutorial(Me) AndAlso Global.TutorialIsland.RestoreOrCreateIslandForPlayer(Me, False) Is Nothing Then
			Me.ClearTutorial()
			MyBase.Hurt(999999F)
			Me.ClearTutorial_PostDeath()
		End If
	End Sub

	' Token: 0x060006DD RID: 1757 RVA: 0x0005268C File Offset: 0x0005088C
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.FromOwner()>
	Private Sub ClientKeepConnectionAlive(msg As Global.BaseEntity.RPCMessage)
		Me.lastTickTime = UnityEngine.Time.time
	End Sub

	' Token: 0x060006DE RID: 1758 RVA: 0x00052699 File Offset: 0x00050899
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.FromOwner()>
	Private Sub ClientLoadingComplete(msg As Global.BaseEntity.RPCMessage)
	End Sub

	' Token: 0x060006DF RID: 1759 RVA: 0x0005269C File Offset: 0x0005089C
	Public Sub PlayerInit(c As Network.Connection)
		Using TimeWarning.[New]("PlayerInit", 10)
			MyBase.CancelInvoke(AddressOf MyBase.KillMessage)
			Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.Connected, True)
			Global.BasePlayer.activePlayerList.Add(Me)
			Global.BasePlayer.bots.Remove(Me)
			Me.userID = c.userid
			Me.UserIDString = Me.userID.ToString()
			Me.displayName = c.username
			c.player = Me
			Me.secondsConnected = 0
			Dim playerTeam As Global.RelationshipManager.PlayerTeam = Global.RelationshipManager.ServerInstance.FindPlayersTeam(Me.userID)
			Me.currentTeam = If((playerTeam IsNot Nothing), playerTeam.teamID, 0UL)
			SingletonComponent(Of ServerMgr).Instance.persistance.SetPlayerName(Me.userID, Me.displayName)
			Me.tickInterpolator.Reset(MyBase.transform.position)
			Me.tickHistory.Reset(MyBase.transform.position)
			Me.eyeHistory.Clear()
			Me.lastTickTime = 0F
			Me.lastInputTime = 0F
			Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.ReceivingSnapshot, True)
			Me.stats.Init()
			MyBase.InvokeRandomized(AddressOf Me.StatSave, UnityEngine.Random.Range(5F, 10F), 30F, UnityEngine.Random.Range(0F, 6F))
			Me.previousLifeStory = SingletonComponent(Of ServerMgr).Instance.persistance.GetLastLifeStory(Me.userID)
			Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.IsAdmin, c.authLevel > 0UI)
			Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.IsDeveloper, DeveloperList.IsDeveloper(Me))
			If Me.IsDead() AndAlso Me.net.SwitchGroup(Global.BaseNetworkable.LimboNetworkGroup) Then
				MyBase.SendNetworkGroupChange()
			End If
			Me.net.OnConnected(c)
			Me.net.StartSubscriber()
			MyBase.SendAsSnapshot(Me.net.connection, False)
			GlobalNetworkHandler.server.StartSendingSnapshot(Me)
			MyBase.ClientRPC(RpcTarget.Player("StartLoading", Me))
			If BaseGameMode.GetActiveGameMode(True) Then
				BaseGameMode.GetActiveGameMode(True).OnPlayerConnected(Me)
			End If
			If Me.net IsNot Nothing Then
				EACServer.OnStartLoading(Me.net.connection)
			End If
			If Me.IsAdmin Then
				If ConVar.AntiHack.noclip_protection <= 0 Then
					Me.ChatMessage("antihack.noclip_protection is disabled!")
				End If
				If ConVar.AntiHack.speedhack_protection <= 0 Then
					Me.ChatMessage("antihack.speedhack_protection is disabled!")
				End If
				If ConVar.AntiHack.flyhack_protection <= 0 Then
					Me.ChatMessage("antihack.flyhack_protection is disabled!")
				End If
				If ConVar.AntiHack.projectile_protection <= 0 Then
					Me.ChatMessage("antihack.projectile_protection is disabled!")
				End If
				If ConVar.AntiHack.melee_protection <= 0 Then
					Me.ChatMessage("antihack.melee_protection is disabled!")
				End If
				If ConVar.AntiHack.eye_protection <= 0 Then
					Me.ChatMessage("antihack.eye_protection is disabled!")
				End If
			End If
			Me.inventory.crafting.SendToOwner()
			If TerrainMeta.Path IsNot Nothing AndAlso TerrainMeta.Path.OceanPatrolFar IsNot Nothing Then
				Me.SendCargoPatrolPath()
			End If
		End Using
	End Sub

	' Token: 0x060006E0 RID: 1760 RVA: 0x000529B4 File Offset: 0x00050BB4
	Public Sub StatSave()
		If Me.stats IsNot Nothing Then
			Me.stats.Save(False)
		End If
	End Sub

	' Token: 0x060006E1 RID: 1761 RVA: 0x000529CA File Offset: 0x00050BCA
	Public Sub SendDeathInformation()
		MyBase.ClientRPC(RpcTarget.Player("OnDied", Me))
	End Sub

	' Token: 0x060006E2 RID: 1762 RVA: 0x000529E0 File Offset: 0x00050BE0
	Public Sub SendRespawnOptions()
		If NexusServer.Started AndAlso ZoneController.Instance.CanRespawnAcrossZones(Me) Then
			Me.<SendRespawnOptions>g__CollectExternalAndSend|409_0()
			Return
		End If
		Dim list As List(Of RespawnInformation.SpawnOptions) = Facepunch.Pool.GetList(Of RespawnInformation.SpawnOptions)()
		Global.BasePlayer.GetRespawnOptionsForPlayer(list, Me.userID)
		Me.<SendRespawnOptions>g__SendToPlayer|409_1(list, False)
	End Sub

	' Token: 0x060006E3 RID: 1763 RVA: 0x00052A28 File Offset: 0x00050C28
	Public Shared Sub GetRespawnOptionsForPlayer(spawnOptions As List(Of RespawnInformation.SpawnOptions), userID As ULong)
		Dim basePlayer As Global.BasePlayer = Global.BasePlayer.FindByID(userID)
		For Each sleepingBag As Global.SleepingBag In Global.SleepingBag.FindForPlayer(userID, True)
			If Not(basePlayer IsNot Nothing) OrElse basePlayer.IsInTutorial = sleepingBag.IsTutorialBag Then
				Dim spawnOptions2 As RespawnInformation.SpawnOptions = Facepunch.Pool.[Get](Of RespawnInformation.SpawnOptions)()
				spawnOptions2.id = sleepingBag.net.ID
				spawnOptions2.name = sleepingBag.niceName
				spawnOptions2.worldPosition = sleepingBag.transform.position
				spawnOptions2.type = If(sleepingBag.isStatic, RespawnInformation.SpawnOptions.RespawnType.[Static], sleepingBag.RespawnType)
				spawnOptions2.unlockSeconds = sleepingBag.GetUnlockSeconds(userID)
				spawnOptions2.respawnState = sleepingBag.GetRespawnState(userID)
				spawnOptions2.mobile = sleepingBag.IsMobile()
				spawnOptions.Add(spawnOptions2)
			End If
		Next
	End Sub

	' Token: 0x060006E4 RID: 1764 RVA: 0x00052AF7 File Offset: 0x00050CF7
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.FromOwner()>
	<Global.BaseEntity.RPC_Server.CallsPerSecond(1UL)>
	Private Sub RequestRespawnInformation(msg As Global.BaseEntity.RPCMessage)
		Me.SendRespawnOptions()
	End Sub

	' Token: 0x170000D3 RID: 211
	' (get) Token: 0x060006E5 RID: 1765 RVA: 0x00052AFF File Offset: 0x00050CFF
	Public ReadOnly Property secondsSleeping As Single
		Get
			If Me.sleepStartTime = -1F OrElse Not Me.IsSleeping() Then
				Return 0F
			End If
			Return UnityEngine.Time.time - Me.sleepStartTime
		End Get
	End Property

	' Token: 0x060006E6 RID: 1766 RVA: 0x00052B28 File Offset: 0x00050D28
	Public Sub ScheduledDeath()
		Dim deathInfo As PlayerLifeStory.DeathInfo = Facepunch.Pool.[Get](Of PlayerLifeStory.DeathInfo)()
		deathInfo.attackerName = "safezone"
		MyBase.Kill(Global.BaseNetworkable.DestroyMode.None)
		Me.lifeStory.deathInfo = deathInfo
		Me.lifeStory.timeDied = CUInt(Epoch.Current)
		Me.LifeStoryEnd()
	End Sub

	' Token: 0x060006E7 RID: 1767 RVA: 0x00052B70 File Offset: 0x00050D70
	Public Overridable Sub StartSleeping()
		If Me.IsSleeping() Then
			Return
		End If
		If Me.IsRestrained Then
			Me.inventory.SetLockedByRestraint(False)
		End If
		If Me.InSafeZone() AndAlso Not MyBase.IsInvoking(AddressOf Me.ScheduledDeath) Then
			MyBase.Invoke(AddressOf Me.ScheduledDeath, NPCAutoTurret.sleeperhostiledelay)
		End If
		Dim baseMountable As BaseMountable = Me.GetMounted()
		If baseMountable IsNot Nothing AndAlso Not Me.AllowSleeperMounting(baseMountable) Then
			Me.EnsureDismounted()
		End If
		Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.Sleeping, True)
		Me.sleepStartTime = UnityEngine.Time.time
		Global.BasePlayer.sleepingPlayerList.TryAdd(Me)
		Global.BasePlayer.bots.Remove(Me)
		MyBase.CancelInvoke(AddressOf Me.InventoryUpdate)
		MyBase.CancelInvoke(AddressOf Me.TeamUpdate)
		MyBase.CancelInvoke(AddressOf Me.UpdateClanLastSeen)
		Me.inventory.loot.Clear()
		Me.inventory.containerMain.OnChanged()
		Me.inventory.containerBelt.OnChanged()
		Me.inventory.containerWear.OnChanged()
		Me.EnablePlayerCollider()
		If Not Me.IsLoadingAfterTransfer() Then
			Me.RemovePlayerRigidbody()
			Me.TurnOffAllLights()
		End If
		Me.SetServerFall(True)
	End Sub

	' Token: 0x060006E8 RID: 1768 RVA: 0x00052CB0 File Offset: 0x00050EB0
	Private Sub TurnOffAllLights()
		Me.LightToggle(False)
		Dim heldEntity As Global.HeldEntity = Me.GetHeldEntity()
		If heldEntity IsNot Nothing Then
			Dim component As TorchWeapon = heldEntity.GetComponent(Of TorchWeapon)()
			If component IsNot Nothing Then
				component.SetIsOn(False)
			End If
		End If
	End Sub

	' Token: 0x060006E9 RID: 1769 RVA: 0x00052CEB File Offset: 0x00050EEB
	Private Sub OnPhysicsNeighbourChanged()
		If Me.IsSleeping() OrElse Me.IsIncapacitated() Then
			MyBase.Invoke(AddressOf Me.DelayedServerFall, 0.05F)
		End If
	End Sub

	' Token: 0x060006EA RID: 1770 RVA: 0x00052D14 File Offset: 0x00050F14
	Private Sub DelayedServerFall()
		Me.SetServerFall(True)
	End Sub

	' Token: 0x060006EB RID: 1771 RVA: 0x00052D20 File Offset: 0x00050F20
	Public Sub SetServerFall(wantsOn As Boolean)
		If wantsOn AndAlso ConVar.Server.playerserverfall Then
			If Not MyBase.IsInvoking(AddressOf Me.ServerFall) Then
				Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.ServerFall, True)
				Me.lastFallTime = UnityEngine.Time.time - Me.fallTickRate
				MyBase.InvokeRandomized(AddressOf Me.ServerFall, 0F, Me.fallTickRate, Me.fallTickRate * 0.1F)
				Me.fallVelocity = Me.estimatedVelocity.y
				Return
			End If
		Else
			MyBase.CancelInvoke(AddressOf Me.ServerFall)
			Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.ServerFall, False)
		End If
	End Sub

	' Token: 0x060006EC RID: 1772 RVA: 0x00052DC4 File Offset: 0x00050FC4
	Public Sub ServerFall()
		If Me.IsDead() OrElse MyBase.HasParent() OrElse (Not Me.IsIncapacitated() AndAlso Not Me.IsSleeping()) Then
			Me.SetServerFall(False)
			Return
		End If
		Dim num As Single = UnityEngine.Time.time - Me.lastFallTime
		Me.lastFallTime = UnityEngine.Time.time
		Dim radius As Single = Me.GetRadius()
		Dim num2 As Single = Me.GetHeight(True) * 0.5F
		Dim num3 As Single = 2.5F
		Dim num4 As Single = 0.5F
		Me.fallVelocity += UnityEngine.Physics.gravity.y * num3 * num4 * num
		Dim num5 As Single = Mathf.Abs(Me.fallVelocity * num)
		Dim origin As Vector3 = MyBase.transform.position + Vector3.up * (radius + num2)
		Dim position As Vector3 = MyBase.transform.position
		Dim vector As Vector3 = MyBase.transform.position
		Dim raycastHit As RaycastHit
		If UnityEngine.Physics.SphereCast(origin, radius, Vector3.down, raycastHit, num5 + num2, 1537286401, QueryTriggerInteraction.Ignore) Then
			Me.SetServerFall(False)
			If raycastHit.distance > num2 Then
				vector += Vector3.down * (raycastHit.distance - num2)
			End If
			Me.ApplyFallDamageFromVelocity(Me.fallVelocity)
			Me.UpdateEstimatedVelocity(vector, vector, num)
			Me.fallVelocity = 0F
		ElseIf UnityEngine.Physics.Raycast(origin, Vector3.down, raycastHit, num5 + radius + num2, 1537286401, QueryTriggerInteraction.Ignore) Then
			Me.SetServerFall(False)
			If raycastHit.distance > num2 - radius Then
				vector += Vector3.down * (raycastHit.distance - num2 - radius)
			End If
			Me.ApplyFallDamageFromVelocity(Me.fallVelocity)
			Me.UpdateEstimatedVelocity(vector, vector, num)
			Me.fallVelocity = 0F
		Else
			vector += Vector3.down * num5
			Me.UpdateEstimatedVelocity(position, vector, num)
			If WaterLevel.Test(vector, True, True, Me) OrElse Global.AntiHack.TestInsideTerrain(vector) Then
				Me.SetServerFall(False)
			End If
		End If
		Me.MovePosition(vector)
	End Sub

	' Token: 0x060006ED RID: 1773 RVA: 0x00052FBD File Offset: 0x000511BD
	Public Sub DelayedRigidbodyDisable()
		Me.RemovePlayerRigidbody()
	End Sub

	' Token: 0x060006EE RID: 1774 RVA: 0x00052FC8 File Offset: 0x000511C8
	Public Overridable Sub EndSleeping()
		If Not Me.IsSleeping() Then
			Return
		End If
		If Me.IsRestrained Then
			Me.inventory.SetLockedByRestraint(True)
		End If
		Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.Sleeping, False)
		Me.sleepStartTime = -1F
		Global.BasePlayer.sleepingPlayerList.Remove(Me)
		If Me.userID < 10000000UL AndAlso Not Global.BasePlayer.bots.Contains(Me) Then
			Global.BasePlayer.bots.Add(Me)
		End If
		MyBase.CancelInvoke(AddressOf Me.ScheduledDeath)
		MyBase.InvokeRepeating(AddressOf Me.InventoryUpdate, 1F, 0.1F * UnityEngine.Random.Range(0.99F, 1.01F))
		If Global.RelationshipManager.TeamsEnabled() Then
			MyBase.InvokeRandomized(AddressOf Me.TeamUpdate, 1F, 4F, 1F)
		End If
		MyBase.InvokeRandomized(AddressOf Me.UpdateClanLastSeen, 300F, 300F, 60F)
		Me.EnablePlayerCollider()
		Me.AddPlayerRigidbody()
		Me.SetServerFall(False)
		If MyBase.HasParent() Then
			MyBase.SetParent(Nothing, True, False)
			MyBase.RemoveFromTriggers()
			MyBase.ForceUpdateTriggers(True, True, True)
		End If
		Me.inventory.containerMain.OnChanged()
		Me.inventory.containerBelt.OnChanged()
		Me.inventory.containerWear.OnChanged()
		EACServer.LogPlayerSpawn(Me)
		If Me.TotalPingCount > 0 Then
			Me.SendPingsToClient()
		End If
		If Global.TutorialIsland.ShouldPlayerBeAskedToStartTutorial(Me) Then
			MyBase.ClientRPC(RpcTarget.Player("PromptToStartTutorial", Me))
		End If
	End Sub

	' Token: 0x060006EF RID: 1775 RVA: 0x00053155 File Offset: 0x00051355
	Public Overridable Sub EndLooting()
		If Me.inventory.loot Then
			Me.inventory.loot.Clear()
		End If
	End Sub

	' Token: 0x060006F0 RID: 1776 RVA: 0x0005317C File Offset: 0x0005137C
	Public Overridable Sub OnDisconnected()
		Me.startTutorialCooldown = 0F
		Me.stats.Save(True)
		Me.EndLooting()
		Me.ClearDesigningAIEntity()
		If Me.IsAlive() OrElse Me.IsSleeping() Then
			Me.StartSleeping()
		Else
			MyBase.Invoke(AddressOf MyBase.KillMessage, 0F)
		End If
		Global.BasePlayer.activePlayerList.Remove(Me)
		Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.Connected, False)
		Me.StopDemoRecording()
		If Me.net IsNot Nothing Then
			Me.net.OnDisconnected()
		End If
		Me.ResetAntiHack()
		Me.RefreshColliderSize(True)
		If BaseGameMode.GetActiveGameMode(True) Then
			BaseGameMode.GetActiveGameMode(True).OnPlayerDisconnected(Me)
		End If
		BaseMission.PlayerDisconnected(Me)
		Dim serverInstance As Global.ClanManager = Global.ClanManager.ServerInstance
		If Me.clanId <> 0L AndAlso serverInstance IsNot Nothing Then
			serverInstance.ClanMemberConnectionsChanged(Me.clanId)
		End If
		Me.UpdateClanLastSeen()
	End Sub

	' Token: 0x060006F1 RID: 1777 RVA: 0x00053261 File Offset: 0x00051461
	Private Sub InventoryUpdate()
		If Me.IsConnected AndAlso Not Me.IsDead() Then
			Me.inventory.ServerUpdate(0.1F)
		End If
	End Sub

	' Token: 0x060006F2 RID: 1778 RVA: 0x00053284 File Offset: 0x00051484
	Public Sub ApplyFallDamageFromVelocity(velocity As Single)
		Dim num As Single = Mathf.InverseLerp(-15F, -100F, velocity)
		If num = 0F Then
			Return
		End If
		Me.metabolism.bleeding.Add(num * 0.5F)
		Dim num2 As Single = num * 500F
		Analytics.Azure.OnFallDamage(Me, velocity, num2)
		MyBase.Hurt(num2, DamageType.Fall, Nothing, True)
		If num2 > 20F AndAlso Me.fallDamageEffect.isValid Then
			Effect.server.Run(Me.fallDamageEffect.resourcePath, MyBase.transform.position, Vector3.zero, Nothing, False, Nothing)
		End If
	End Sub

	' Token: 0x060006F3 RID: 1779 RVA: 0x00053318 File Offset: 0x00051518
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.FromOwner()>
	Private Sub OnPlayerLanded(msg As Global.BaseEntity.RPCMessage)
		Dim num As Single = msg.read.Float()
		If Single.IsNaN(num) OrElse Single.IsInfinity(num) Then
			Return
		End If
		If Not ConVar.AntiHack.serverside_fall_damage Then
			Me.ApplyFallDamageFromVelocity(num)
			Me.fallVelocity = 0F
		End If
	End Sub

	' Token: 0x060006F4 RID: 1780 RVA: 0x0005335C File Offset: 0x0005155C
	Public Sub SendGlobalSnapshot()
		Using TimeWarning.[New]("SendGlobalSnapshot", 10)
			Me.EnterVisibility(Network.Net.sv.visibility.[Get](0UI))
		End Using
	End Sub

	' Token: 0x060006F5 RID: 1781 RVA: 0x000533A8 File Offset: 0x000515A8
	Public Sub SendFullSnapshot()
		Using TimeWarning.[New]("SendFullSnapshot", 0)
			For Each group As Group In Me.net.subscriber.subscribed
				If group.ID <> 0UI Then
					Me.EnterVisibility(group)
				End If
			Next
		End Using
	End Sub

	' Token: 0x060006F6 RID: 1782 RVA: 0x00053430 File Offset: 0x00051630
	Public Overrides Sub OnNetworkGroupLeave(group As Group)
		MyBase.OnNetworkGroupLeave(group)
		Me.LeaveVisibility(group)
	End Sub

	' Token: 0x060006F7 RID: 1783 RVA: 0x00053440 File Offset: 0x00051640
	Private Sub LeaveVisibility(group As Group)
		ServerMgr.OnLeaveVisibility(Me.net.connection, group)
		Me.ClearEntityQueue(group)
	End Sub

	' Token: 0x060006F8 RID: 1784 RVA: 0x0005345A File Offset: 0x0005165A
	Public Overrides Sub OnNetworkGroupEnter(group As Group)
		MyBase.OnNetworkGroupEnter(group)
		Me.EnterVisibility(group)
	End Sub

	' Token: 0x060006F9 RID: 1785 RVA: 0x0005346A File Offset: 0x0005166A
	Private Sub EnterVisibility(group As Group)
		ServerMgr.OnEnterVisibility(Me.net.connection, group)
		Me.SendSnapshots(group.networkables)
	End Sub

	' Token: 0x060006FA RID: 1786 RVA: 0x00053489 File Offset: 0x00051689
	Public Sub CheckDeathCondition(Optional info As HitInfo = Nothing)
		Assert.IsTrue(MyBase.isServer, "CheckDeathCondition called on client!")
		If Me.IsSpectating() Then
			Return
		End If
		If Me.IsDead() Then
			Return
		End If
		If Me.metabolism.ShouldDie() Then
			Me.Die(info)
		End If
	End Sub

	' Token: 0x060006FB RID: 1787 RVA: 0x000534C4 File Offset: 0x000516C4
	Public Overridable Function CreateCorpse(flagsOnDeath As Global.BasePlayer.PlayerFlags, posOnDeath As Vector3, rotOnDeath As Quaternion, triggersOnDeath As List(Of TriggerBase), Optional forceServerSide As Boolean = False) As BaseCorpse
		Using TimeWarning.[New]("Create corpse", 0)
			Dim strCorpsePrefab As String
			If ConVar.Physics.serversideragdolls OrElse forceServerSide Then
				strCorpsePrefab = "assets/prefabs/player/player_corpse_new.prefab"
			Else
				strCorpsePrefab = "assets/prefabs/player/player_corpse.prefab"
			End If
			Dim flag As Boolean = False
			If ConVar.[Global].cinematicGingerbreadCorpses Then
				For Each item As Global.Item In Me.inventory.containerWear.itemList
					Dim itemCorpseOverride As ItemCorpseOverride
					If item IsNot Nothing AndAlso item.info.TryGetComponent(Of ItemCorpseOverride)(itemCorpseOverride) Then
						strCorpsePrefab = If((Global.BasePlayer.<CreateCorpse>g__GetFloatBasedOnUserID|439_0(Me.userID, 4332UL) > 0.5F), itemCorpseOverride.FemaleCorpse.resourcePath, itemCorpseOverride.MaleCorpse.resourcePath)
						flag = itemCorpseOverride.BlockWearableCopy
						Exit For
					End If
				Next
			End If
			Dim playerCorpse As PlayerCorpse = TryCast(MyBase.DropCorpse(strCorpsePrefab, posOnDeath, rotOnDeath, flagsOnDeath, Me.modelState), PlayerCorpse)
			If playerCorpse Then
				playerCorpse.SetFlag(Global.BaseEntity.Flags.Reserved5, Me.HasPlayerFlag(Global.BasePlayer.PlayerFlags.DisplaySash), False, True)
				If Not flag Then
					playerCorpse.TakeFrom(Me, New Global.ItemContainer() { Me.inventory.containerMain, Me.inventory.containerWear, Me.inventory.containerBelt })
				End If
				playerCorpse.playerName = Me.displayName
				playerCorpse.streamerName = RandomUsernames.[Get](Me.userID)
				playerCorpse.playerSteamID = Me.userID
				playerCorpse.underwearSkin = Me.GetUnderwearSkin()
				If Not triggersOnDeath.IsNullOrEmpty() Then
					For Each triggerBase As TriggerBase In triggersOnDeath
						Dim triggerParent As TriggerParent = TryCast(triggerBase, TriggerParent)
						If triggerParent IsNot Nothing Then
							triggerParent.ForceParentEarly(playerCorpse)
						End If
					Next
				End If
				playerCorpse.Spawn()
				playerCorpse.TakeChildren(Me)
				Dim component As ResourceDispenser = playerCorpse.GetComponent(Of ResourceDispenser)()
				Dim num As Integer = 2
				If Me.lifeStory IsNot Nothing Then
					num += Mathf.Clamp(Mathf.FloorToInt(Me.lifeStory.secondsAlive / 180F), 0, 20)
				End If
				component.containedItems.Add(New ItemAmount(ItemManager.FindItemDefinition("fat.animal"), CSng(num)))
				Return playerCorpse
			End If
		End Using
		Return Nothing
	End Function

	' Token: 0x060006FC RID: 1788 RVA: 0x0005374C File Offset: 0x0005194C
	Public Overrides Sub OnKilled(info As HitInfo)
		Dim flagsOnDeath As Global.BasePlayer.PlayerFlags = Me.playerFlags
		Dim position As Vector3 = MyBase.transform.position
		Dim list As List(Of TriggerBase) = Facepunch.Pool.GetList(Of TriggerBase)()
		If Me.triggers IsNot Nothing Then
			For Each triggerBase As TriggerBase In Me.triggers
				If triggerBase IsNot Nothing Then
					list.Add(triggerBase)
				End If
			Next
		End If
		Dim baseMountable As BaseMountable = Me.GetMounted()
		Dim b As Vector3 = Vector3.zero
		Dim rotOnDeath As Quaternion
		If baseMountable.IsValid() Then
			rotOnDeath = baseMountable.mountAnchor.rotation
			b = baseMountable.GetMountRagdollVelocity(Me)
		Else
			rotOnDeath = Quaternion.Euler(MyBase.transform.eulerAngles.x, Me.eyes.bodyRotation.eulerAngles.y, MyBase.transform.eulerAngles.z)
		End If
		Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.Unused2, False)
		Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.Unused1, False)
		Me.EnsureDismounted()
		Me.EndSleeping()
		Me.EndLooting()
		Me.stats.Add("deaths", 1, Global.Stats.All)
		If info IsNot Nothing AndAlso info.InitiatorPlayer IsNot Nothing AndAlso Not info.InitiatorPlayer.IsNpc AndAlso Not Me.IsNpc Then
			Global.RelationshipManager.ServerInstance.SetSeen(info.InitiatorPlayer, Me)
			Global.RelationshipManager.ServerInstance.SetSeen(Me, info.InitiatorPlayer)
			Global.RelationshipManager.ServerInstance.SetRelationship(Me, info.InitiatorPlayer, Global.RelationshipManager.RelationshipType.Enemy, 1, False)
			Me.HandleClanPlayerKilled(info.InitiatorPlayer)
		End If
		If BaseGameMode.GetActiveGameMode(True) Then
			Dim instigator As Global.BasePlayer = If((info Is Nothing), Nothing, info.InitiatorPlayer)
			BaseGameMode.GetActiveGameMode(True).OnPlayerDeath(instigator, Me, info)
		End If
		BaseMission.PlayerKilled(Me)
		Me.DisablePlayerCollider()
		Me.RemovePlayerRigidbody()
		Dim list2 As List(Of Global.BasePlayer) = Facepunch.Pool.GetList(Of Global.BasePlayer)()
		If Me.IsIncapacitated() Then
			For Each basePlayer As Global.BasePlayer In Global.BasePlayer.activePlayerList
				If basePlayer IsNot Nothing AndAlso basePlayer.inventory IsNot Nothing AndAlso basePlayer.inventory.loot IsNot Nothing AndAlso basePlayer.inventory.loot.entitySource Is Me Then
					list2.Add(basePlayer)
				End If
			Next
		End If
		Dim flag As Boolean = Me.IsWounded()
		Me.StopWounded(Nothing)
		If Me.inventory.crafting IsNot Nothing Then
			Me.inventory.crafting.CancelAll(True)
		End If
		EACServer.LogPlayerDespawn(Me)
		Dim flag2 As Boolean = Me.eyes.HeadRay().direction.y > 0.8F
		Dim flag3 As Boolean = False
		If flag2 Then
			Dim direction As Vector3 = -Me.eyes.MovementForward()
			Dim raycastHit As RaycastHit
			If GamePhysics.Trace(New Ray(Me.eyes.position, direction), 0F, raycastHit, 1F, 2097152, QueryTriggerInteraction.UseGlobal, Nothing) Then
				flag3 = True
			End If
		End If
		Dim baseCorpse As BaseCorpse = Me.CreateCorpse(flagsOnDeath, position, rotOnDeath, list, flag2 AndAlso flag3)
		If baseCorpse IsNot Nothing Then
			If baseCorpse.CorpseIsRagdoll AndAlso baseMountable IsNot Nothing Then
				Dim baseVehicle As Global.BaseVehicle = baseMountable.VehicleParent()
				If baseVehicle IsNot Nothing AndAlso baseVehicle.mountedPlayerRagdolls = Global.BaseVehicle.RagdollMode.FallThrough Then
					baseCorpse.gameObject.SetIgnoreCollisions(baseVehicle.gameObject, True)
				End If
			End If
			If info IsNot Nothing Then
				Dim component As Rigidbody = baseCorpse.GetComponent(Of Rigidbody)()
				If component IsNot Nothing Then
					Dim d As Single = If(baseCorpse.CorpseIsRagdoll, 5F, 1F)
					Dim a As Vector3 = (info.attackNormal + Vector3.up * 0.5F).normalized * d
					component.AddForce(a + b, ForceMode.VelocityChange)
				End If
			End If
			Dim playerCorpse As PlayerCorpse = TryCast(baseCorpse, PlayerCorpse)
			If playerCorpse IsNot Nothing AndAlso playerCorpse.containers IsNot Nothing Then
				For Each basePlayer2 As Global.BasePlayer In list2
					If Not(basePlayer2 Is Nothing) Then
						basePlayer2.inventory.loot.StartLootingEntity(playerCorpse, True)
						For Each itemContainer As Global.ItemContainer In playerCorpse.containers
							If itemContainer IsNot Nothing Then
								basePlayer2.inventory.loot.AddContainer(itemContainer)
							End If
						Next
						basePlayer2.inventory.loot.SendImmediate()
					End If
				Next
			End If
		End If
		Facepunch.Pool.FreeList(Of Global.BasePlayer)(list2)
		Me.inventory.Strip()
		If flag AndAlso Me.lastDamage = DamageType.Suicide AndAlso Me.cachedNonSuicideHitInfo IsNot Nothing Then
			info = Me.cachedNonSuicideHitInfo
			Me.lastDamage = info.damageTypes.GetMajorityDamageType()
		End If
		Me.cachedNonSuicideHitInfo = Nothing
		If Me.lastDamage = DamageType.Fall Then
			Me.stats.Add("death_fall", 1, Global.Stats.Steam)
		End If
		Dim message As String
		Dim msg As String
		If info IsNot Nothing Then
			If info.Initiator Then
				If info.Initiator Is Me Then
					message = String.Concat(New String() { Me.ToString(), " was killed by ", Me.lastDamage.ToString(), " at ", MyBase.transform.position.ToString() })
					msg = "You died: killed by " + Me.lastDamage.ToString()
					If Me.lastDamage = DamageType.Suicide Then
						Analytics.Server.Death("suicide", Me.ServerPosition, Analytics.Server.DeathType.Player)
						Me.stats.Add("death_suicide", 1, Global.Stats.All)
					Else
						Analytics.Server.Death("selfinflicted", Me.ServerPosition, Analytics.Server.DeathType.Player)
						Me.stats.Add("death_selfinflicted", 1, Global.Stats.Steam)
					End If
				Else
					If TypeOf info.Initiator Is Global.BasePlayer Then
						Dim basePlayer3 As Global.BasePlayer = info.Initiator.ToPlayer()
						message = String.Concat(New String() { Me.ToString(), " was killed by ", basePlayer3.ToString(), " at ", MyBase.transform.position.ToString() })
						Dim array As String() = New String(4) {}
						array(0) = "You died: killed by "
						array(1) = basePlayer3.displayName
						array(2) = " ("
						Dim num As Integer = 3
						Dim encryptedValue As Global.BasePlayer.EncryptedValue(Of ULong) = basePlayer3.userID
						array(num) = encryptedValue.ToString()
						array(4) = ")"
						msg = String.Concat(array)
						basePlayer3.stats.Add("kill_player", 1, Global.Stats.All)
						basePlayer3.LifeStoryKill(Me)
						Me.OnKilledByPlayer(basePlayer3)
						If Me.lastDamage = DamageType.Fun_Water Then
							basePlayer3.GiveAchievement("SUMMER_LIQUIDATOR", False)
							Dim liquidWeapon As LiquidWeapon = TryCast(basePlayer3.GetHeldEntity(), LiquidWeapon)
							If liquidWeapon IsNot Nothing AndAlso liquidWeapon.RequiresPumping AndAlso liquidWeapon.PressureFraction <= liquidWeapon.MinimumPressureFraction Then
								basePlayer3.GiveAchievement("SUMMER_NO_PRESSURE", False)
							End If
						ElseIf GameInfo.HasAchievements AndAlso Me.lastDamage = DamageType.Explosion AndAlso info.WeaponPrefab IsNot Nothing AndAlso info.WeaponPrefab.ShortPrefabName.Contains("mlrs") AndAlso basePlayer3 IsNot Nothing Then
							basePlayer3.stats.Add("mlrs_kills", 1, Global.Stats.All)
							basePlayer3.stats.Save(True)
						End If
						Analytics.Azure.OnPlayerDeath(Me, basePlayer3)
					Else
						message = String.Concat(New String() { Me.ToString(), " was killed by ", info.Initiator.ShortPrefabName, " (", info.Initiator.Categorize(), ") at ", MyBase.transform.position.ToString() })
						msg = "You died: killed by " + info.Initiator.Categorize()
						Me.stats.Add("death_" + info.Initiator.Categorize(), 1, Global.Stats.Steam)
					End If
					If Not Me.IsNpc Then
						Analytics.Server.Death(info.Initiator, info.WeaponPrefab, Me.ServerPosition)
					End If
				End If
			ElseIf Me.lastDamage = DamageType.Fall Then
				message = Me.ToString() + " was killed by fall at " + MyBase.transform.position.ToString()
				msg = "You died: killed by fall"
				Analytics.Server.Death("fall", Me.ServerPosition, Analytics.Server.DeathType.Player)
			Else
				message = String.Concat(New String() { Me.ToString(), " was killed by ", info.damageTypes.GetMajorityDamageType().ToString(), " at ", MyBase.transform.position.ToString() })
				msg = "You died: " + info.damageTypes.GetMajorityDamageType().ToString()
			End If
		Else
			message = Me.ToString() + " died (" + Me.lastDamage.ToString() + ")"
			msg = "You died: " + Me.lastDamage.ToString()
		End If
		Using TimeWarning.[New]("LogMessage", 0)
			DebugEx.Log(message, StackTraceLogType.None)
			Me.ConsoleMessage(msg)
		End Using
		If Me.net.connection Is Nothing AndAlso If((info IsNot Nothing), info.Initiator, Nothing) IsNot Nothing AndAlso info.Initiator IsNot Me Then
			CompanionServer.Util.SendDeathNotification(Me, info.Initiator)
		End If
		MyBase.SendNetworkUpdateImmediate(False)
		Me.LifeStoryLogDeath(info, Me.lastDamage)
		Me.Server_LogDeathMarker(MyBase.transform.position)
		Me.LifeStoryEnd()
		Me.LastBlockColourChangeId = 0UI
		If Me.net.connection Is Nothing Then
			MyBase.Invoke(AddressOf MyBase.KillMessage, 0F)
		Else
			Me.SendRespawnOptions()
			Me.SendDeathInformation()
			Me.stats.Save(False)
		End If
		Facepunch.Pool.FreeList(Of TriggerBase)(list)
	End Sub

	' Token: 0x060006FD RID: 1789 RVA: 0x000541AC File Offset: 0x000523AC
	Public Sub RespawnAt(position As Vector3, rotation As Quaternion, Optional spawnPointEntity As Global.BaseEntity = Nothing)
		Dim activeGameMode As BaseGameMode = BaseGameMode.GetActiveGameMode(True)
		If activeGameMode AndAlso Not activeGameMode.CanPlayerRespawn(Me) Then
			Return
		End If
		Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.Wounded, False)
		Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.Unused2, False)
		Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.Unused1, False)
		Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.ReceivingSnapshot, True)
		Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.DisplaySash, False)
		Me.respawnId = Guid.NewGuid().ToString("N")
		ServerPerformance.spawns += 1UL
		MyBase.SetParent(Nothing, True, False)
		MyBase.transform.SetPositionAndRotation(position, rotation)
		Me.tickInterpolator.Reset(position)
		Me.tickHistory.Reset(position)
		Me.eyeHistory.Clear()
		Me.estimatedVelocity = Vector3.zero
		Me.estimatedSpeed = 0F
		Me.estimatedSpeed2D = 0F
		Me.lastTickTime = 0F
		Me.StopWounded(Nothing)
		Me.ResetWoundingVars()
		Me.StopSpectating()
		Me.UpdateNetworkGroup()
		Me.EnablePlayerCollider()
		Me.RemovePlayerRigidbody()
		Me.StartSleeping()
		Me.LifeStoryStart()
		Me.metabolism.Reset()
		If Me.modifiers IsNot Nothing Then
			Me.modifiers.RemoveAll()
		End If
		Me.InitializeHealth(Me.StartHealth(), Me.StartMaxHealth())
		Dim flag As Boolean = False
		If ConVar.Server.respawnWithLoadout Then
			Dim infoString As String = Me.GetInfoString("client.respawnloadout", String.Empty)
			Dim savedLoadout As Inventory.SavedLoadout
			If Not String.IsNullOrEmpty(infoString) AndAlso Inventory.LoadLoadout(infoString, savedLoadout) Then
				savedLoadout.LoadItemsOnTo(Me)
				flag = True
			End If
		End If
		If Not flag Then
			Me.inventory.GiveDefaultItems()
		End If
		MyBase.SendNetworkUpdateImmediate(False)
		MyBase.ClientRPC(RpcTarget.Player("StartLoading", Me))
		Analytics.Azure.OnPlayerRespawned(Me, spawnPointEntity)
		If activeGameMode Then
			BaseGameMode.GetActiveGameMode(True).OnPlayerRespawn(Me)
		End If
		If Me.IsConnected Then
			EACServer.OnStartLoading(Me.net.connection)
		End If
		Me.ProcessMissionEvent(BaseMission.MissionEventType.RESPAWN, 0, 0F)
	End Sub

	' Token: 0x060006FE RID: 1790 RVA: 0x00054390 File Offset: 0x00052590
	Public Sub Respawn()
		Dim spawnPoint As Global.BasePlayer.SpawnPoint = ServerMgr.FindSpawnPoint(Me)
		If ConVar.Server.respawnAtDeathPosition AndAlso Me.ServerCurrentDeathNote IsNot Nothing Then
			spawnPoint.pos = Me.ServerCurrentDeathNote.worldPosition
		End If
		Me.RespawnAt(spawnPoint.pos, spawnPoint.rot, Nothing)
	End Sub

	' Token: 0x060006FF RID: 1791 RVA: 0x000543D8 File Offset: 0x000525D8
	Public Function IsImmortalTo(info As HitInfo) As Boolean
		If Me.IsGod() Then
			Return True
		End If
		If Me.WoundingCausingImmortality(info) Then
			Return True
		End If
		Dim mountedVehicle As Global.BaseVehicle = Me.GetMountedVehicle()
		If mountedVehicle IsNot Nothing AndAlso mountedVehicle.ignoreDamageFromOutside Then
			Dim initiatorPlayer As Global.BasePlayer = info.InitiatorPlayer
			If initiatorPlayer IsNot Nothing AndAlso initiatorPlayer.GetMountedVehicle() IsNot mountedVehicle Then
				Return True
			End If
		End If
		If Me.IsInTutorial Then
			info.InitiatorPlayer IsNot Me
			Return False
		End If
		Return False
	End Function

	' Token: 0x06000700 RID: 1792 RVA: 0x0005444A File Offset: 0x0005264A
	Public Function TimeAlive() As Single
		Return Me.lifeStory.secondsAlive
	End Function

	' Token: 0x06000701 RID: 1793 RVA: 0x00054458 File Offset: 0x00052658
	Public Overrides Sub Hurt(info As HitInfo)
		If Me.IsDead() Then
			Return
		End If
		If MyBase.IsTransferProtected() Then
			Return
		End If
		If Me.IsImmortalTo(info) AndAlso info.damageTypes.Total() >= 0F Then
			Return
		End If
		If ConVar.Server.pve AndAlso Not Me.IsNpc AndAlso info.Initiator AndAlso TypeOf info.Initiator Is Global.BasePlayer AndAlso info.Initiator IsNot Me Then
			TryCast(info.Initiator, Global.BasePlayer).Hurt(info.damageTypes.Total(), DamageType.Generic, Nothing, True)
			Return
		End If
		If info.damageTypes.Has(DamageType.Fun_Water) Then
			Dim flag As Boolean = True
			Dim activeItem As Global.Item = Me.GetActiveItem()
			If activeItem IsNot Nothing AndAlso (activeItem.info.shortname = "gun.water" OrElse activeItem.info.shortname = "pistol.water") Then
				Dim value As Single = Me.metabolism.wetness.value
				Me.metabolism.wetness.Add(ConVar.Server.funWaterWetnessGain)
				Dim flag2 As Boolean = Me.metabolism.wetness.value >= ConVar.Server.funWaterDamageThreshold
				flag = Not flag2
				If info.InitiatorPlayer IsNot Nothing Then
					If flag2 AndAlso value < ConVar.Server.funWaterDamageThreshold Then
						info.InitiatorPlayer.GiveAchievement("SUMMER_SOAKED", False)
					End If
					If Me.metabolism.radiation_level.Fraction() > 0.2F AndAlso Not String.IsNullOrEmpty("SUMMER_RADICAL") Then
						info.InitiatorPlayer.GiveAchievement("SUMMER_RADICAL", False)
					End If
				End If
			End If
			If flag Then
				info.damageTypes.Scale(DamageType.Fun_Water, 0F)
			End If
		End If
		If info.damageTypes.[Get](DamageType.Drowned) > 5F AndAlso Me.drownEffect.isValid Then
			Effect.server.Run(Me.drownEffect.resourcePath, Me, StringPool.[Get]("head"), Vector3.zero, Vector3.zero, Nothing, False, Nothing)
		End If
		If Me.modifiers IsNot Nothing Then
			If info.damageTypes.Has(DamageType.Radiation) Then
				info.damageTypes.Scale(DamageType.Radiation, 1F - Mathf.Clamp01(Me.modifiers.GetValue(Global.Modifier.ModifierType.Radiation_Resistance, 0F)))
			End If
			If info.damageTypes.Has(DamageType.RadiationExposure) Then
				info.damageTypes.Scale(DamageType.RadiationExposure, 1F - Mathf.Clamp01(Me.modifiers.GetValue(Global.Modifier.ModifierType.Radiation_Exposure_Resistance, 0F)))
			End If
		End If
		Me.metabolism.pending_health.Subtract(info.damageTypes.Total() * 10F)
		Dim initiatorPlayer As Global.BasePlayer = info.InitiatorPlayer
		If initiatorPlayer AndAlso initiatorPlayer IsNot Me Then
			If initiatorPlayer.InSafeZone() OrElse Me.InSafeZone() Then
				initiatorPlayer.MarkHostileFor(300F)
			End If
			If initiatorPlayer.InSafeZone() AndAlso Not initiatorPlayer.IsNpc Then
				info.damageTypes.ScaleAll(0F)
				Return
			End If
			If initiatorPlayer.IsNpc AndAlso initiatorPlayer.Family = BaseNpc.AiStatistics.FamilyEnum.Murderer AndAlso info.damageTypes.[Get](DamageType.Explosion) > 0F Then
				info.damageTypes.ScaleAll(Halloween.scarecrow_beancan_vs_player_dmg_modifier)
			End If
		End If
		MyBase.Hurt(info)
		If BaseGameMode.GetActiveGameMode(True) Then
			Dim instigator As Global.BasePlayer = If((info Is Nothing), Nothing, info.InitiatorPlayer)
			BaseGameMode.GetActiveGameMode(True).OnPlayerHurt(instigator, Me, info)
		End If
		If Me.IsRestrained AndAlso info.damageTypes.GetMajorityDamageType().InterruptsRestraintMinigame() Then
			Dim handcuffs As Handcuffs = TryCast(Me.GetHeldEntity(), Handcuffs)
			If handcuffs IsNot Nothing Then
				handcuffs.InterruptUnlockMiniGame(True)
			End If
		End If
		EACServer.LogPlayerTakeDamage(Me, info)
		Me.metabolism.SendChangesToClient()
		If info.PointStart <> Vector3.zero AndAlso (info.damageTypes.Total() >= 0F OrElse Me.IsGod()) Then
			Dim arg As Integer = CInt(info.damageTypes.GetMajorityDamageType())
			If info.Weapon IsNot Nothing AndAlso info.damageTypes.Has(DamageType.Bullet) Then
				Dim component As Global.BaseProjectile = info.Weapon.GetComponent(Of Global.BaseProjectile)()
				If component IsNot Nothing AndAlso component.IsSilenced() Then
					arg = 12
				End If
			End If
			MyBase.ClientRPC(Of Vector3, Integer, Integer)(RpcTarget.PlayerAndSpectators("DirectionalDamage", Me), info.PointStart, arg, Mathf.CeilToInt(info.damageTypes.Total()))
		End If
		Me.cachedNonSuicideHitInfo = info
	End Sub

	' Token: 0x06000702 RID: 1794 RVA: 0x00054890 File Offset: 0x00052A90
	Public Overrides Sub Heal(amount As Single)
		If Me.IsCrawling() Then
			Dim health As Single = MyBase.health
			MyBase.Heal(amount)
			Me.healingWhileCrawling += MyBase.health - health
		Else
			MyBase.Heal(amount)
		End If
		Me.ProcessMissionEvent(BaseMission.MissionEventType.HEAL, 0, amount)
	End Sub

	' Token: 0x170000D4 RID: 212
	' (get) Token: 0x06000703 RID: 1795 RVA: 0x000548DB File Offset: 0x00052ADB
	Public Shared ReadOnly Iterator Property allPlayerList As IEnumerable(Of Global.BasePlayer)
		Get
			For Each basePlayer As Global.BasePlayer In Global.BasePlayer.sleepingPlayerList
				Yield basePlayer
			Next
			Dim enumerator As ListHashSet(Of Global.BasePlayer).Enumerator = Nothing
			For Each basePlayer2 As Global.BasePlayer In Global.BasePlayer.activePlayerList
				Yield basePlayer2
			Next
			enumerator = Nothing
			Return
			Return
		End Get
	End Property

	' Token: 0x06000704 RID: 1796 RVA: 0x000548E4 File Offset: 0x00052AE4
	Public Shared Function FindBot(userId As ULong) As Global.BasePlayer
		For Each basePlayer As Global.BasePlayer In Global.BasePlayer.bots
			If basePlayer.userID = userId Then
				Return basePlayer
			End If
		Next
		Return Global.BasePlayer.FindBotClosestMatch(userId.ToString())
	End Function

	' Token: 0x06000705 RID: 1797 RVA: 0x00054950 File Offset: 0x00052B50
	Public Shared Function FindBotClosestMatch(name As String) As Global.BasePlayer
		If String.IsNullOrEmpty(name) Then
			Return Nothing
		End If
		For Each basePlayer As Global.BasePlayer In Global.BasePlayer.bots
			If basePlayer.displayName.Contains(name) Then
				Return basePlayer
			End If
		Next
		Return Nothing
	End Function

	' Token: 0x06000706 RID: 1798 RVA: 0x000549BC File Offset: 0x00052BBC
	Public Shared Function FindByID(userID As ULong) As Global.BasePlayer
		Dim result As Global.BasePlayer
		Using TimeWarning.[New]("BasePlayer.FindByID", 0)
			For Each basePlayer As Global.BasePlayer In Global.BasePlayer.activePlayerList
				If basePlayer.userID = userID Then
					Return basePlayer
				End If
			Next
			result = Nothing
		End Using
		Return result
	End Function

	' Token: 0x06000707 RID: 1799 RVA: 0x00054A40 File Offset: 0x00052C40
	Public Shared Function TryFindByID(userID As ULong, <System.Runtime.InteropServices.OutAttribute()> ByRef basePlayer As Global.BasePlayer) As Boolean
		basePlayer = Global.BasePlayer.FindByID(userID)
		Return basePlayer IsNot Nothing
	End Function

	' Token: 0x06000708 RID: 1800 RVA: 0x00054A54 File Offset: 0x00052C54
	Public Shared Function FindSleeping(userID As ULong) As Global.BasePlayer
		Dim result As Global.BasePlayer
		Using TimeWarning.[New]("BasePlayer.FindSleeping", 0)
			For Each basePlayer As Global.BasePlayer In Global.BasePlayer.sleepingPlayerList
				If basePlayer.userID = userID Then
					Return basePlayer
				End If
			Next
			result = Nothing
		End Using
		Return result
	End Function

	' Token: 0x06000709 RID: 1801 RVA: 0x00054AD8 File Offset: 0x00052CD8
	Public Shared Function FindAwakeOrSleepingByID(userID As ULong) As Global.BasePlayer
		If userID = 0UL Then
			Return Nothing
		End If
		Dim basePlayer As Global.BasePlayer = Global.BasePlayer.FindByID(userID)
		If Not(basePlayer IsNot Nothing) Then
			Return Global.BasePlayer.FindSleeping(userID)
		End If
		Return basePlayer
	End Function

	' Token: 0x0600070A RID: 1802 RVA: 0x00054B02 File Offset: 0x00052D02
	Public Sub Command(strCommand As String, ParamArray arguments As Object())
		If Me.net.connection Is Nothing Then
			Return
		End If
		ConsoleNetwork.SendClientCommand(Me.net.connection, strCommand, arguments)
	End Sub

	' Token: 0x0600070B RID: 1803 RVA: 0x00054B24 File Offset: 0x00052D24
	Public Overrides Sub OnInvalidPosition()
		If Me.IsDead() Then
			Return
		End If
		Me.Die(Nothing)
	End Sub

	' Token: 0x0600070C RID: 1804 RVA: 0x00054B38 File Offset: 0x00052D38
	Private Shared Function Find(strNameOrIDOrIP As String, list As IEnumerable(Of Global.BasePlayer)) As Global.BasePlayer
		Dim basePlayer As Global.BasePlayer = list.FirstOrDefault(Function(x As Global.BasePlayer) x.UserIDString = strNameOrIDOrIP)
		If basePlayer Then
			Return basePlayer
		End If
		Dim basePlayer2 As Global.BasePlayer = list.FirstOrDefault(Function(x As Global.BasePlayer) x.displayName.StartsWith(strNameOrIDOrIP, StringComparison.CurrentCultureIgnoreCase))
		If basePlayer2 Then
			Return basePlayer2
		End If
		Dim basePlayer3 As Global.BasePlayer = list.FirstOrDefault(Function(x As Global.BasePlayer) x.net IsNot Nothing AndAlso x.net.connection IsNot Nothing AndAlso x.net.connection.ipaddress = strNameOrIDOrIP)
		If basePlayer3 Then
			Return basePlayer3
		End If
		Return Nothing
	End Function

	' Token: 0x0600070D RID: 1805 RVA: 0x00054BAA File Offset: 0x00052DAA
	Public Shared Function Find(strNameOrIDOrIP As String) As Global.BasePlayer
		Return Global.BasePlayer.Find(strNameOrIDOrIP, Global.BasePlayer.activePlayerList)
	End Function

	' Token: 0x0600070E RID: 1806 RVA: 0x00054BB7 File Offset: 0x00052DB7
	Public Shared Function FindSleeping(strNameOrIDOrIP As String) As Global.BasePlayer
		Return Global.BasePlayer.Find(strNameOrIDOrIP, Global.BasePlayer.sleepingPlayerList)
	End Function

	' Token: 0x0600070F RID: 1807 RVA: 0x00054BC4 File Offset: 0x00052DC4
	Public Shared Function FindAwakeOrSleeping(strNameOrIDOrIP As String) As Global.BasePlayer
		Return Global.BasePlayer.Find(strNameOrIDOrIP, Global.BasePlayer.allPlayerList)
	End Function

	' Token: 0x06000710 RID: 1808 RVA: 0x00054BD1 File Offset: 0x00052DD1
	Public Sub SendConsoleCommand(command As String, ParamArray obj As Object())
		ConsoleNetwork.SendClientCommand(Me.net.connection, command, obj)
	End Sub

	' Token: 0x06000711 RID: 1809 RVA: 0x00054BE5 File Offset: 0x00052DE5
	Public Sub UpdateRadiation(fAmount As Single)
		Me.metabolism.radiation_level.Increase(fAmount)
	End Sub

	' Token: 0x06000712 RID: 1810 RVA: 0x00054BF8 File Offset: 0x00052DF8
	Public Overrides Function RadiationExposureFraction() As Single
		Dim num As Single = Mathf.Clamp(Me.baseProtection.amounts(17), 0F, 1F)
		Return 1F - num
	End Function

	' Token: 0x06000713 RID: 1811 RVA: 0x00054C2A File Offset: 0x00052E2A
	Public Overrides Function RadiationProtection() As Single
		Return Me.baseProtection.amounts(17) * 100F
	End Function

	' Token: 0x06000714 RID: 1812 RVA: 0x00054C40 File Offset: 0x00052E40
	Public Overrides Sub OnHealthChanged(oldvalue As Single, newvalue As Single)
		MyBase.OnHealthChanged(oldvalue, newvalue)
		If Not MyBase.isServer Then
			Return
		End If
		If oldvalue > newvalue Then
			Me.LifeStoryHurt(oldvalue - newvalue)
		Else
			Me.LifeStoryHeal(newvalue - oldvalue)
		End If
		Me.metabolism.isDirty = True
	End Sub

	' Token: 0x06000715 RID: 1813 RVA: 0x00054C77 File Offset: 0x00052E77
	Public Sub SV_ClothingChanged()
		Me.UpdateProtectionFromClothing()
		Me.UpdateMoveSpeedFromClothing()
	End Sub

	' Token: 0x06000716 RID: 1814 RVA: 0x00054C85 File Offset: 0x00052E85
	Public Function IsNoob() As Boolean
		Return Not Me.HasPlayerFlag(Global.BasePlayer.PlayerFlags.DisplaySash)
	End Function

	' Token: 0x06000717 RID: 1815 RVA: 0x00054C98 File Offset: 0x00052E98
	Public Function HasHostileItem() As Boolean
		Dim result As Boolean
		Using TimeWarning.[New]("BasePlayer.HasHostileItem", 0)
			For Each item As Global.Item In Me.inventory.containerBelt.itemList
				If Me.IsHostileItem(item) Then
					Return True
				End If
			Next
			For Each item2 As Global.Item In Me.inventory.containerMain.itemList
				If Me.IsHostileItem(item2) Then
					Return True
				End If
			Next
			result = False
		End Using
		Return result
	End Function

	' Token: 0x06000718 RID: 1816 RVA: 0x00054D78 File Offset: 0x00052F78
	Public Overrides Sub GiveItem(item As Global.Item, Optional reason As Global.BaseEntity.GiveItemReason = Global.BaseEntity.GiveItemReason.Generic)
		If reason = Global.BaseEntity.GiveItemReason.ResourceHarvested Then
			Me.stats.Add(String.Format("harvest.{0}", item.info.shortname), item.amount, CType(6, Global.Stats))
		End If
		If reason = Global.BaseEntity.GiveItemReason.ResourceHarvested OrElse reason = Global.BaseEntity.GiveItemReason.Crafted Then
			Me.ProcessMissionEvent(BaseMission.MissionEventType.HARVEST, item.info.itemid, CSng(item.amount))
		End If
		Dim amount As Integer = item.amount
		If Not Me.inventory.GiveItem(item, Nothing) Then
			item.Drop(Me.inventory.containerMain.dropPosition, Me.inventory.containerMain.dropVelocity, Nothing)
			Return
		End If
		Dim infoBool As Boolean = Me.GetInfoBool("global.streamermode", False)
		Dim name As String = item.GetName(New Boolean?(infoBool))
		If Not String.IsNullOrEmpty(name) Then
			Me.Command("note.inv", New Object() { item.info.itemid, amount, name, CInt(reason) })
			Return
		End If
		Me.Command("note.inv", New Object() { item.info.itemid, amount, String.Empty, CInt(reason) })
	End Sub

	' Token: 0x06000719 RID: 1817 RVA: 0x00054EB6 File Offset: 0x000530B6
	Public Overrides Sub AttackerInfo(info As PlayerLifeStory.DeathInfo)
		info.attackerName = Me.displayName
		info.attackerSteamID = Me.userID
	End Sub

	' Token: 0x0600071A RID: 1818 RVA: 0x00054ED5 File Offset: 0x000530D5
	Public Sub InvalidateWorkbenchCache()
		Me.nextCheckTime = 0F
	End Sub

	' Token: 0x0600071B RID: 1819 RVA: 0x00054EE2 File Offset: 0x000530E2
	Public Function GetCachedCraftLevelWorkbench() As Workbench
		Return Me._cachedWorkbench
	End Function

	' Token: 0x170000D5 RID: 213
	' (get) Token: 0x0600071C RID: 1820 RVA: 0x00054EEC File Offset: 0x000530EC
	Public ReadOnly Property currentCraftLevel As Single
		Get
			If Me.triggers Is Nothing Then
				Me._cachedWorkbench = Nothing
				Return 0F
			End If
			If Me.nextCheckTime > UnityEngine.Time.realtimeSinceStartup Then
				Return Me.cachedCraftLevel
			End If
			Me._cachedWorkbench = Nothing
			Me.nextCheckTime = UnityEngine.Time.realtimeSinceStartup + UnityEngine.Random.Range(0.4F, 0.5F)
			Dim num As Single = 0F
			For i As Integer = 0 To Me.triggers.Count - 1
				Dim triggerWorkbench As TriggerWorkbench = TryCast(Me.triggers(i), TriggerWorkbench)
				If Not(triggerWorkbench Is Nothing) AndAlso Not(triggerWorkbench.parentBench Is Nothing) AndAlso triggerWorkbench.parentBench.IsVisible(Me.eyes.position, Single.PositiveInfinity) Then
					Me._cachedWorkbench = triggerWorkbench.parentBench
					Dim num2 As Single = triggerWorkbench.WorkbenchLevel()
					If num2 > num Then
						num = num2
					End If
				End If
			Next
			Me.cachedCraftLevel = num
			Return num
		End Get
	End Property

	' Token: 0x170000D6 RID: 214
	' (get) Token: 0x0600071D RID: 1821 RVA: 0x00054FC8 File Offset: 0x000531C8
	Public ReadOnly Property currentComfort As Single
		Get
			Dim num As Single = 0F
			If Me.isMounted Then
				num = Me.GetMounted().GetComfort()
			End If
			If Me.triggers Is Nothing Then
				Return num
			End If
			For i As Integer = 0 To Me.triggers.Count - 1
				Dim triggerComfort As TriggerComfort = TryCast(Me.triggers(i), TriggerComfort)
				If Not(triggerComfort Is Nothing) Then
					Dim num2 As Single = triggerComfort.CalculateComfort(MyBase.transform.position, Me)
					If num2 > num Then
						num = num2
					End If
				End If
			Next
			Return num
		End Get
	End Property

	' Token: 0x0600071E RID: 1822 RVA: 0x00055044 File Offset: 0x00053244
	Public Overridable Function ShouldDropActiveItem() As Boolean
		Return True
	End Function

	' Token: 0x0600071F RID: 1823 RVA: 0x00055048 File Offset: 0x00053248
	Public Overrides Sub Die(Optional info As HitInfo = Nothing)
		Using TimeWarning.[New]("Player.Die", 0)
			If Not Me.IsDead() Then
				Dim restraintItem As Handcuffs = Me.Belt.GetRestraintItem()
				If restraintItem IsNot Nothing Then
					restraintItem.HeldWhenOwnerDied(Me)
				End If
				If Me.Belt IsNot Nothing AndAlso Me.ShouldDropActiveItem() Then
					Dim vector As Vector3 = New Vector3(UnityEngine.Random.Range(-2F, 2F), 0.2F, UnityEngine.Random.Range(-2F, 2F))
					Me.Belt.DropActive(Me.GetDropPosition(), Me.GetInheritedDropVelocity() + vector.normalized * 3F)
					Me.inventory.DropBackpackOnDeath()
				End If
				If Not Me.WoundInsteadOfDying(info) Then
					Global.SleepingBag.OnPlayerDeath(Me)
					MyBase.Die(info)
				End If
			End If
		End Using
	End Sub

	' Token: 0x06000720 RID: 1824 RVA: 0x00055130 File Offset: 0x00053330
	Public Sub Kick(reason As String)
		If Not Me.IsConnected Then
			Return
		End If
		Network.Net.sv.Kick(Me.net.connection, reason, False)
	End Sub

	' Token: 0x06000721 RID: 1825 RVA: 0x00055152 File Offset: 0x00053352
	Public Overrides Function GetDropPosition() As Vector3
		Return Me.eyes.position
	End Function

	' Token: 0x06000722 RID: 1826 RVA: 0x0005515F File Offset: 0x0005335F
	Public Overrides Function GetDropVelocity() As Vector3
		Return Me.GetInheritedDropVelocity() + Me.eyes.BodyForward() * 4F + Vector3Ex.Range(-0.5F, 0.5F)
	End Function

	' Token: 0x06000723 RID: 1827 RVA: 0x00055198 File Offset: 0x00053398
	Public Overrides Sub ApplyInheritedVelocity(velocity As Vector3)
		Dim parentEntity As Global.BaseEntity = MyBase.GetParentEntity()
		If parentEntity IsNot Nothing Then
			MyBase.ClientRPC(Of Vector3, NetworkableId)(RpcTarget.Player("SetInheritedVelocity", Me), parentEntity.transform.InverseTransformDirection(velocity), parentEntity.net.ID)
		Else
			MyBase.ClientRPC(Of Vector3)(RpcTarget.Player("SetInheritedVelocity", Me), velocity)
		End If
		Me.PauseSpeedHackDetection(1F)
	End Sub

	' Token: 0x06000724 RID: 1828 RVA: 0x000551FC File Offset: 0x000533FC
	Public Overridable Sub SetInfo(key As String, val As String)
		If Not Me.IsConnected Then
			Return
		End If
		Me.net.connection.info.[Set](key, val)
	End Sub

	' Token: 0x06000725 RID: 1829 RVA: 0x0005521E File Offset: 0x0005341E
	Public Overridable Function GetInfoInt(key As String, defaultVal As Integer) As Integer
		If Not Me.IsConnected Then
			Return defaultVal
		End If
		Return Me.net.connection.info.GetInt(key, defaultVal)
	End Function

	' Token: 0x06000726 RID: 1830 RVA: 0x00055241 File Offset: 0x00053441
	Public Overridable Function GetInfoBool(key As String, defaultVal As Boolean) As Boolean
		If Not Me.IsConnected Then
			Return defaultVal
		End If
		Return Me.net.connection.info.GetBool(key, defaultVal)
	End Function

	' Token: 0x06000727 RID: 1831 RVA: 0x00055264 File Offset: 0x00053464
	Public Overridable Function GetInfoString(key As String, defaultVal As String) As String
		If Not Me.IsConnected Then
			Return defaultVal
		End If
		Return Me.net.connection.info.GetString(key, defaultVal)
	End Function

	' Token: 0x06000728 RID: 1832 RVA: 0x00055288 File Offset: 0x00053488
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.CallsPerSecond(1UL)>
	Public Sub PerformanceReport(msg As Global.BaseEntity.RPCMessage)
		Dim text As String = msg.read.[String](256, False)
		Dim text2 As String = msg.read.StringRaw(8388608, False)
		Dim clientPerformanceReport As ClientPerformanceReport = JsonConvert.DeserializeObject(Of ClientPerformanceReport)(text2)
		If clientPerformanceReport.user_id <> Me.UserIDString Then
			DebugEx.Log(String.Format("Client performance report from {0} has incorrect user_id ({1})", Me, Me.UserIDString), StackTraceLogType.None)
			Return
		End If
		If text = "json" Then
			DebugEx.Log(text2, StackTraceLogType.None)
			Return
		End If
		If text = "legacy" Then
			Dim text3 As String = (clientPerformanceReport.memory_managed_heap.ToString() + "MB").PadRight(9)
			Dim text4 As String = (clientPerformanceReport.memory_system.ToString() + "MB").PadRight(9)
			Dim text5 As String = (clientPerformanceReport.fps.ToString("0") + "FPS").PadRight(8)
			Dim text6 As String = CLng(clientPerformanceReport.fps).FormatSeconds().PadRight(9)
			Dim text7 As String = Me.UserIDString.PadRight(20)
			Dim text8 As String = clientPerformanceReport.streamer_mode.ToString().PadRight(7)
			DebugEx.Log(String.Concat(New String() { text3, text4, text5, text6, text8, text7, Me.displayName }), StackTraceLogType.None)
			Return
		End If
		If Not(text = "none") Then
			If text = "rcon" Then
				RCon.Broadcast(RCon.LogType.ClientPerf, text2)
				Return
			End If
			Debug.LogError("Unknown PerformanceReport format '" + text + "'")
		End If
	End Sub

	' Token: 0x06000729 RID: 1833 RVA: 0x00055418 File Offset: 0x00053618
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.CallsPerSecond(1UL)>
	Public Sub PerformanceReport_Frametime(msg As Global.BaseEntity.RPCMessage)
		Dim request_id As Integer = msg.read.Int32()
		Dim start_frame As Integer = msg.read.Int32()
		Dim num As Integer = msg.read.Int32()
		Dim list As List(Of Integer) = Facepunch.Pool.GetList(Of Integer)()
		For i As Integer = 0 To num - 1
			list.Add(ProtocolParser.ReadInt32(msg.read))
		Next
		Dim clientFrametimeReport As ClientFrametimeReport = New ClientFrametimeReport()
		clientFrametimeReport.frame_times = list
		clientFrametimeReport.request_id = request_id
		clientFrametimeReport.start_frame = start_frame
		DebugEx.Log(JsonConvert.SerializeObject(clientFrametimeReport), StackTraceLogType.None)
		Facepunch.Pool.FreeList(Of Integer)(clientFrametimeReport.frame_times)
	End Sub

	' Token: 0x0600072A RID: 1834 RVA: 0x000554A0 File Offset: 0x000536A0
	Public Overrides Function ShouldNetworkTo(player As Global.BasePlayer) As Boolean
		If player Is Me Then
			Return True
		End If
		If Me.IsSpectating() AndAlso player IsNot Me Then
			Return False
		End If
		Dim flag As Boolean = MyBase.ShouldNetworkTo(player)
		If ServerOcclusion.OcclusionEnabled AndAlso flag Then
			flag = Me.OcclusionLineOfSight(player)
		End If
		Return flag
	End Function

	' Token: 0x0600072B RID: 1835 RVA: 0x000554E8 File Offset: 0x000536E8
	Private Function OcclusionLineOfSight(player As Global.BasePlayer) As Boolean
		If Me.OcclusionGetRecentlySeen(player) Then
			Return True
		End If
		If Me.OcclusionShouldSeeAllPlayers() Then
			Global.BasePlayer.OcclusionPlayerFound(Me, player, False)
			Return True
		End If
		If Me.SubGrid.GetDistance(player.SubGrid) < ServerOcclusion.MinOcclusionDistance Then
			Global.BasePlayer.OcclusionPlayerFound(Me, player, False)
			Return True
		End If
		If player.SubGrid.Equals(Nothing) Then
			Global.BasePlayer.OcclusionPlayerFound(Me, player, False)
			Return True
		End If
		Dim flag As Boolean
		If ServerOcclusion.OcclusionCache.TryGetValue(New ValueTuple(Of ServerOcclusion.SubGrid, ServerOcclusion.SubGrid)(Me.SubGrid, player.SubGrid), flag) Then
			If flag Then
				Global.BasePlayer.OcclusionPlayerFound(Me, player, True)
				Return True
			End If
			Global.BasePlayer.OcclusionPlayerLost(Me, player, True)
			Return False
		Else
			Dim flag2 As Boolean = ServerOcclusion.PathBetweenDirectBresenham(Me.SubGrid, player.SubGrid)
			If Not flag2 Then
				Dim power As Integer = If((Not Me.SubGrid.Equals(Me.EstimatedSubGrid) AndAlso Not player.SubGrid.Equals(player.EstimatedSubGrid)), 3, 2)
				ServerOcclusion.SetFromGrids(Me.SubGrid, player.SubGrid, power)
				flag2 = ServerOcclusion.PathBetweenFloodFill(Me.SubGrid, player.SubGrid)
			End If
			If flag2 Then
				Global.BasePlayer.OcclusionPlayerFound(Me, player, True)
				Return True
			End If
			Global.BasePlayer.OcclusionPlayerLost(Me, player, True)
			Return False
		End If
	End Function

	' Token: 0x0600072C RID: 1836 RVA: 0x00055614 File Offset: 0x00053814
	Private Shared Sub OcclusionPlayerFound(player1 As Global.BasePlayer, player2 As Global.BasePlayer, Optional cache As Boolean = True)
		Global.BasePlayer.<OcclusionPlayerFound>g__UpdateVisibility|498_0(player1, player2)
		If Not player1.OcclusionShouldSeeAllPlayers() Then
			Global.BasePlayer.<OcclusionPlayerFound>g__UpdateVisibility|498_0(player2, player1)
		End If
		If cache Then
			ServerOcclusion.OcclusionCache.TryAdd(New ValueTuple(Of ServerOcclusion.SubGrid, ServerOcclusion.SubGrid)(player1.SubGrid, player2.SubGrid), True)
			ServerOcclusion.OcclusionCache.TryAdd(New ValueTuple(Of ServerOcclusion.SubGrid, ServerOcclusion.SubGrid)(player2.SubGrid, player1.SubGrid), True)
		End If
	End Sub

	' Token: 0x0600072D RID: 1837 RVA: 0x00055674 File Offset: 0x00053874
	Private Shared Sub OcclusionPlayerLost(player1 As Global.BasePlayer, player2 As Global.BasePlayer, Optional cache As Boolean = True)
		Global.BasePlayer.<OcclusionPlayerLost>g__UpdateVisibility|499_0(player1, player2)
		If Not player2.OcclusionShouldSeeAllPlayers() Then
			Global.BasePlayer.<OcclusionPlayerLost>g__UpdateVisibility|499_0(player2, player1)
		End If
		If cache Then
			ServerOcclusion.OcclusionCache.TryAdd(New ValueTuple(Of ServerOcclusion.SubGrid, ServerOcclusion.SubGrid)(player1.SubGrid, player2.SubGrid), False)
			ServerOcclusion.OcclusionCache.TryAdd(New ValueTuple(Of ServerOcclusion.SubGrid, ServerOcclusion.SubGrid)(player2.SubGrid, player1.SubGrid), False)
		End If
	End Sub

	' Token: 0x0600072E RID: 1838 RVA: 0x000556D4 File Offset: 0x000538D4
	Private Function OcclusionGetRecentlySeen(player As Global.BasePlayer) As Boolean
		Dim num As Single
		Return Me.lastPlayerVisibility.TryGetValue(player, num) AndAlso Me.GetNetworkTime() - num < ServerOcclusion.OcclusionFade
	End Function

	' Token: 0x0600072F RID: 1839 RVA: 0x00055702 File Offset: 0x00053902
	Private Function OcclusionShouldSeeAllPlayers() As Boolean
		Return Me.IsSpectating() OrElse (ConVar.AntiHack.server_occlusion_admin_bypass AndAlso (Me.IsAdmin OrElse Me.IsDeveloper))
	End Function

	' Token: 0x06000730 RID: 1840 RVA: 0x00055728 File Offset: 0x00053928
	Friend Sub GiveAchievement(name As String, Optional allowTutorial As Boolean = False)
		If GameInfo.HasAchievements AndAlso (Not Me.IsInTutorial OrElse allowTutorial) Then
			MyBase.ClientRPC(Of String)(RpcTarget.Player("RecieveAchievement", Me), name)
		End If
	End Sub

	' Token: 0x06000731 RID: 1841 RVA: 0x00055750 File Offset: 0x00053950
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.CallsPerSecond(1UL)>
	Public Sub OnPlayerReported(msg As Global.BaseEntity.RPCMessage)
		Dim text As String = msg.read.[String](256, False)
		Dim message As String = msg.read.StringMultiLine(2048, False)
		Dim type As String = msg.read.[String](256, False)
		Dim text2 As String = msg.read.[String](256, False)
		Dim text3 As String = msg.read.[String](256, False)
		DebugEx.Log(String.Format("[PlayerReport] {0} reported {1}[{2}] - ""{3}""", New Object() { Me, text3, text2, text }), StackTraceLogType.None)
		RCon.Broadcast(RCon.LogType.Report, New With{ Key .PlayerId = Me.UserIDString, Key .PlayerName = Me.displayName, Key .TargetId = text2, Key .TargetName = text3, Key .Subject = text, Key .Message = message, Key .Type = type })
	End Sub

	' Token: 0x06000732 RID: 1842 RVA: 0x000557FC File Offset: 0x000539FC
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.CallsPerSecond(1UL)>
	Public Sub OnFeedbackReport(msg As Global.BaseEntity.RPCMessage)
		If Not ConVar.Server.printReportsToConsole AndAlso String.IsNullOrEmpty(ConVar.Server.reportsServerEndpoint) Then
			Return
		End If
		Dim text As String = msg.read.[String](256, False)
		Dim text2 As String = msg.read.StringMultiLine(2048, False)
		Dim reportType As ReportType = CType(Mathf.Clamp(msg.read.Int32(), 0, 5), ReportType)
		If ConVar.Server.printReportsToConsole Then
			DebugEx.Log(String.Format("[FeedbackReport] {0} reported {1} - ""{2}"" ""{3}""", New Object() { Me, reportType, text, text2 }), StackTraceLogType.None)
			RCon.Broadcast(RCon.LogType.Report, New With{ Key .PlayerId = Me.UserIDString, Key .PlayerName = Me.displayName, Key .Subject = text, Key .Message = text2, Key .Type = reportType })
		End If
		If Not String.IsNullOrEmpty(ConVar.Server.reportsServerEndpoint) Then
			Dim image As String = msg.read.StringMultiLine(60000, False)
			Dim feedback As Facepunch.Models.Feedback = New Facepunch.Models.Feedback() With { .Type = reportType, .Message = text2, .Subject = text }
			feedback.AppInfo.Image = image
			Facepunch.Feedback.ServerReport(ConVar.Server.reportsServerEndpoint, Me.userID, ConVar.Server.reportsServerEndpointKey, feedback)
		End If
	End Sub

	' Token: 0x06000733 RID: 1843 RVA: 0x0005590C File Offset: 0x00053B0C
	Public Sub StartDemoRecording()
		If Me.net Is Nothing OrElse Me.net.connection Is Nothing Then
			Return
		End If
		If Me.net.connection.IsRecording Then
			Return
		End If
		Dim text As String = String.Format("demos/{0}/{1:yyyy-MM-dd-hhmmss}.dem", Me.UserIDString, DateTime.Now)
		Debug.Log(Me.ToString() + " recording started: " + text)
		Me.net.connection.StartRecording(text, New Demo.Header() With { .version = Demo.Version, .level = UnityEngine.Application.loadedLevelName, .levelSeed = Global.World.Seed, .levelSize = Global.World.Size, .checksum = Global.World.Checksum, .localclient = Me.userID, .position = Me.eyes.position, .rotation = Me.eyes.HeadForward(), .levelUrl = Global.World.Url, .recordedTime = DateTime.Now.ToBinary() })
		MyBase.SendNetworkUpdateImmediate(False)
		Me.SendGlobalSnapshot()
		Me.SendFullSnapshot()
		Me.SendEntityUpdate()
		TreeManager.SendSnapshot(Me)
		ServerMgr.SendReplicatedVars(Me.net.connection)
		MyBase.InvokeRepeating(AddressOf Me.MonitorDemoRecording, 10F, 10F)
	End Sub

	' Token: 0x06000734 RID: 1844 RVA: 0x00055A60 File Offset: 0x00053C60
	Public Sub StopDemoRecording()
		If Me.net Is Nothing OrElse Me.net.connection Is Nothing Then
			Return
		End If
		If Not Me.net.connection.IsRecording Then
			Return
		End If
		Debug.Log(Me.ToString() + " recording stopped: " + Me.net.connection.RecordFilename)
		Me.net.connection.StopRecording()
		MyBase.CancelInvoke(AddressOf Me.MonitorDemoRecording)
	End Sub

	' Token: 0x06000735 RID: 1845 RVA: 0x00055AE0 File Offset: 0x00053CE0
	Public Sub MonitorDemoRecording()
		If Me.net Is Nothing OrElse Me.net.connection Is Nothing Then
			Return
		End If
		If Not Me.net.connection.IsRecording Then
			Return
		End If
		If Me.net.connection.RecordTimeElapsed.TotalSeconds >= CDbl(Demo.splitseconds) OrElse CSng(Me.net.connection.RecordFilesize) >= Demo.splitmegabytes * 1024F * 1024F Then
			Me.StopDemoRecording()
			Me.StartDemoRecording()
		End If
	End Sub

	' Token: 0x06000736 RID: 1846 RVA: 0x00055B66 File Offset: 0x00053D66
	Public Sub InvalidateCachedPeristantPlayer()
		Me.cachedPersistantPlayer = Nothing
	End Sub

	' Token: 0x170000D7 RID: 215
	' (get) Token: 0x06000737 RID: 1847 RVA: 0x00055B6F File Offset: 0x00053D6F
	' (set) Token: 0x06000738 RID: 1848 RVA: 0x00055B9F File Offset: 0x00053D9F
	Public Property PersistantPlayerInfo As PersistantPlayer
		Get
			If Me.cachedPersistantPlayer Is Nothing Then
				Me.cachedPersistantPlayer = SingletonComponent(Of ServerMgr).Instance.persistance.GetPlayerInfo(Me.userID)
			End If
			Return Me.cachedPersistantPlayer
		End Get
		Set(value As PersistantPlayer)
			If value Is Nothing Then
				Throw New ArgumentNullException("value")
			End If
			Me.cachedPersistantPlayer = value
			SingletonComponent(Of ServerMgr).Instance.persistance.SetPlayerInfo(Me.userID, value)
		End Set
	End Property

	' Token: 0x06000739 RID: 1849 RVA: 0x00055BD4 File Offset: 0x00053DD4
	Public Function IsPlayerVisibleToUs(otherPlayer As Global.BasePlayer, fromOffset As Vector3, layerMask As Integer) As Boolean
		If otherPlayer Is Nothing Then
			Return False
		End If
		Dim vector As Vector3
		If Me.isMounted Then
			vector = Me.eyes.worldMountedPosition
		ElseIf Me.IsDucked() Then
			vector = Me.eyes.worldCrouchedPosition
		ElseIf Me.IsCrawling() Then
			vector = Me.eyes.worldCrawlingPosition
		Else
			vector = Me.eyes.worldStandingPosition
		End If
		vector += fromOffset
		Return(otherPlayer.IsVisibleSpecificLayers(vector, otherPlayer.CenterPoint(), layerMask, Single.PositiveInfinity) OrElse otherPlayer.IsVisibleSpecificLayers(vector, otherPlayer.transform.position, layerMask, Single.PositiveInfinity) OrElse otherPlayer.IsVisibleSpecificLayers(vector, otherPlayer.eyes.position, layerMask, Single.PositiveInfinity)) AndAlso (MyBase.IsVisibleSpecificLayers(otherPlayer.CenterPoint(), vector, layerMask, Single.PositiveInfinity) OrElse MyBase.IsVisibleSpecificLayers(otherPlayer.transform.position, vector, layerMask, Single.PositiveInfinity) OrElse MyBase.IsVisibleSpecificLayers(otherPlayer.eyes.position, vector, layerMask, Single.PositiveInfinity))
	End Function

	' Token: 0x0600073A RID: 1850 RVA: 0x00055CD9 File Offset: 0x00053ED9
	Protected Overridable Sub OnKilledByPlayer(p As Global.BasePlayer)
	End Sub

	' Token: 0x0600073B RID: 1851 RVA: 0x00055CDC File Offset: 0x00053EDC
	Public Function GetIdealSlot(player As Global.BasePlayer, container As Global.ItemContainer, item As Global.Item) As Integer Implements IIdealSlotEntity.GetIdealSlot
		If container.HasFlag(Global.ItemContainer.Flag.Clothing) Then
			If item.IsBackpack() Then
				Return Global.ItemContainer.BackpackSlotIndex
			End If
			If item.info.isWearable Then
				Using enumerator As List(Of Global.Item).Enumerator = container.itemList.GetEnumerator()
					While enumerator.MoveNext()
						Dim item2 As Global.Item = enumerator.Current
						If Not item2.info.ItemModWearable.CanExistWith(item.info.ItemModWearable) AndAlso item2.position = Global.ItemContainer.BackpackSlotIndex = item.IsBackpack() Then
							Return item2.position
						End If
					End While
					Return -1
				End Using
				Return -1
			End If
			Return -1
		End If
		Return -1
	End Function

	' Token: 0x0600073C RID: 1852 RVA: 0x00055D90 File Offset: 0x00053F90
	Public Function GetIdealContainer(looter As Global.BasePlayer, item As Global.Item, modifier As ItemMoveModifier) As ItemContainerId Implements IIdealSlotEntity.GetIdealContainer
		Dim flag As Boolean = Not modifier.HasFlag(ItemMoveModifier.Alt) AndAlso looter.inventory.loot.containers.Count > 0
		Dim parent As Global.ItemContainer = item.parent
		Dim activeItem As Global.Item = looter.GetActiveItem()
		Dim backpackWithInventory As Global.Item = Me.inventory.GetBackpackWithInventory()
		Dim flag2 As Boolean = backpackWithInventory IsNot Nothing AndAlso backpackWithInventory Is item.parentItem
		Dim flag3 As Boolean = False
		If modifier.HasFlag(ItemMoveModifier.BackpackOpen) AndAlso looter Is Me AndAlso backpackWithInventory IsNot Nothing Then
			If backpackWithInventory.contents.HasSpaceFor(item) Then
				If Not flag Then
					If item.parentItem Is Nothing OrElse Not item.parentItem.IsBackpack() OrElse item.parentItem.parent IsNot Me.inventory.containerWear Then
						Return backpackWithInventory.contents.uid
					End If
				ElseIf Me.inventory.loot.FindItem(item.uid) IsNot Nothing AndAlso Not Me.inventory.containerMain.HasSpaceFor(item) Then
					Return backpackWithInventory.contents.uid
				End If
			Else
				flag3 = True
			End If
		End If
		If activeItem IsNot Nothing AndAlso Not flag3 AndAlso Not flag AndAlso activeItem.contents IsNot Nothing AndAlso activeItem.contents IsNot item.parent AndAlso activeItem.contents.capacity > 0 AndAlso activeItem.contents.CanAcceptItem(item, -1) = Global.ItemContainer.CanAcceptResult.CanAccept Then
			Return activeItem.contents.uid
		End If
		If item.info.isWearable AndAlso item.info.ItemModWearable.equipOnRightClick AndAlso item.parent IsNot Me.inventory.containerWear AndAlso Not flag AndAlso Not flag2 Then
			If flag3 Then
				Return ItemContainerId.Invalid
			End If
			If backpackWithInventory Is Nothing OrElse item.parent IsNot backpackWithInventory.contents Then
				Return Me.inventory.containerWear.uid
			End If
		End If
		If parent Is Me.inventory.containerMain Then
			If flag Then
				Return Nothing
			End If
			Return Me.inventory.containerBelt.uid
		Else
			If parent Is Me.inventory.containerWear Then
				Return Me.inventory.containerMain.uid
			End If
			If parent Is Me.inventory.containerBelt Then
				Return Me.inventory.containerMain.uid
			End If
			Return Nothing
		End If
	End Function

	' Token: 0x0600073D RID: 1853 RVA: 0x00055FCC File Offset: 0x000541CC
	Private Function GetVehicleParent() As Global.BaseVehicle
		Dim mountedVehicle As Global.BaseVehicle = Me.GetMountedVehicle()
		If mountedVehicle IsNot Nothing Then
			Return mountedVehicle
		End If
		Dim parentEntity As Global.BaseEntity = MyBase.GetParentEntity()
		If parentEntity IsNot Nothing Then
			Dim baseVehicle As Global.BaseVehicle = TryCast(parentEntity, Global.BaseVehicle)
			If baseVehicle IsNot Nothing Then
				Return baseVehicle
			End If
		End If
		Return Nothing
	End Function

	' Token: 0x0600073E RID: 1854 RVA: 0x00056008 File Offset: 0x00054208
	Private Sub RemoveLoadingPlayerFlag()
		If Not Me.IsLoadingAfterTransfer() Then
			Return
		End If
		Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.LoadingAfterTransfer, False)
		If Me.IsSleeping() Then
			Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.Sleeping, False)
			Me.StartSleeping()
		End If
	End Sub

	' Token: 0x0600073F RID: 1855 RVA: 0x00056038 File Offset: 0x00054238
	Public Function InNoRespawnZone() As Boolean
		Dim flag As Boolean = False
		Dim position As Vector3 = MyBase.transform.position
		If Me.triggers IsNot Nothing Then
			For i As Integer = 0 To Me.triggers.Count - 1
				Dim triggerNoRespawnZone As TriggerNoRespawnZone = TryCast(Me.triggers(i), TriggerNoRespawnZone)
				If Not(triggerNoRespawnZone Is Nothing) Then
					flag = triggerNoRespawnZone.InNoRespawnZone(position, False)
					If flag Then
						Exit For
					End If
				End If
			Next
		End If
		Return flag
	End Function

	' Token: 0x06000740 RID: 1856 RVA: 0x0005609C File Offset: 0x0005429C
	Private Sub SendCargoPatrolPath()
		If Not Global.BaseBoat.generate_paths Then
			Return
		End If
		If Global.BasePlayer.cachedOceanPaths Is Nothing Then
			Global.BasePlayer.cachedOceanPaths = Facepunch.Pool.[Get](Of OceanPaths)()
			Global.BasePlayer.cachedOceanPaths.cargoPatrolPath = TerrainMeta.Path.OceanPatrolFar
			Global.BasePlayer.cachedOceanPaths.harborApproaches = New List(Of VectorList)()
			For i As Integer = 0 To Global.CargoShip.TotalAvailableHarborDockingPaths - 1
				Dim vectorList As VectorList = New VectorList()
				vectorList.vectorPoints = Global.CargoShip.GetCargoApproachPath(i)
				Global.BasePlayer.cachedOceanPaths.harborApproaches.Add(vectorList)
			Next
		End If
		MyBase.ClientRPCPlayer(Of OceanPaths)(Nothing, Me, "ReceiveCargoPatrolPath", Global.BasePlayer.cachedOceanPaths)
	End Sub

	' Token: 0x06000741 RID: 1857 RVA: 0x0005612C File Offset: 0x0005432C
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.CallsPerSecond(5UL)>
	<Global.BaseEntity.RPC_Server.MaxDistance(3F)>
	<Global.BaseEntity.RPC_Server.IsVisible(3F)>
	Private Sub RPC_ReqDoPush(rpc As Global.BaseEntity.RPCMessage)
		If Me.IsSleeping() OrElse Me.IsDead() OrElse Not Me.IsRestrained Then
			Return
		End If
		Dim player As Global.BasePlayer = rpc.player
		If player Is Nothing Then
			Return
		End If
		If player Is Me Then
			Return
		End If
		Dim handcuffs As Handcuffs = TryCast(Me.GetHeldEntity(), Handcuffs)
		If handcuffs IsNot Nothing Then
			handcuffs.InterruptUnlockMiniGame(True)
			handcuffs.RepairOnPush()
		End If
		If Me.isMounted Then
			Dim baseMountable As BaseMountable = Me.GetMounted()
			If baseMountable IsNot Nothing Then
				baseMountable.DismountPlayer(Me, False)
				Return
			End If
		End If
		Dim vector As Vector3 = player.eyes.BodyForward() * 10F
		vector.y = 0F
		vector += Vector3.up * 3F
		MyBase.ClientRPC(Of Vector3)(RpcTarget.Player("RPC_DoPush", Me), vector)
		MyBase.Hurt(Handcuffs.restrainedPushDamage, DamageType.Generic, player, False)
	End Sub

	' Token: 0x06000742 RID: 1858 RVA: 0x00056208 File Offset: 0x00054408
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.CallsPerSecond(5UL)>
	<Global.BaseEntity.RPC_Server.MaxDistance(3F)>
	<Global.BaseEntity.RPC_Server.IsVisible(3F)>
	Private Sub RPC_ReqRemoveCuffs(rpc As Global.BaseEntity.RPCMessage)
		If Me.IsDead() OrElse Not Me.IsRestrained Then
			Return
		End If
		Dim player As Global.BasePlayer = rpc.player
		If player Is Nothing Then
			Return
		End If
		Dim handcuffs As Handcuffs = TryCast(Me.GetHeldEntity(), Handcuffs)
		If handcuffs IsNot Nothing Then
			handcuffs.UnlockAndReturnToPlayer(player)
		End If
	End Sub

	' Token: 0x06000743 RID: 1859 RVA: 0x00056254 File Offset: 0x00054454
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.CallsPerSecond(5UL)>
	<Global.BaseEntity.RPC_Server.MaxDistance(3F)>
	<Global.BaseEntity.RPC_Server.IsVisible(3F)>
	Private Sub RPC_ReqRemoveHood(rpc As Global.BaseEntity.RPCMessage)
		Dim player As Global.BasePlayer = rpc.player
		If player Is Nothing Then
			Return
		End If
		Me.RemoveAndReturnPrisonerHood(player)
	End Sub

	' Token: 0x06000744 RID: 1860 RVA: 0x0005627C File Offset: 0x0005447C
	Private Sub RemoveAndReturnPrisonerHood(returnToPlayer As Global.BasePlayer)
		If returnToPlayer Is Nothing Then
			Return
		End If
		If Me.IsDead() OrElse Not Me.IsRestrained Then
			Return
		End If
		Dim equippedPrisonerHoodItem As Global.Item = Me.inventory.GetEquippedPrisonerHoodItem()
		If equippedPrisonerHoodItem Is Nothing Then
			Return
		End If
		Dim locked As Boolean = Me.inventory.containerWear.IsLocked()
		Me.inventory.containerWear.SetLocked(False)
		returnToPlayer.GiveItem(equippedPrisonerHoodItem, Global.BaseEntity.GiveItemReason.Generic)
		Me.inventory.containerWear.SetLocked(locked)
	End Sub

	' Token: 0x06000745 RID: 1861 RVA: 0x000562F0 File Offset: 0x000544F0
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.CallsPerSecond(5UL)>
	<Global.BaseEntity.RPC_Server.MaxDistance(3F)>
	<Global.BaseEntity.RPC_Server.IsVisible(3F)>
	Private Sub RPC_ReqEquipHood(rpc As Global.BaseEntity.RPCMessage)
		Dim player As Global.BasePlayer = rpc.player
		If player Is Nothing Then
			Return
		End If
		Me.EquipPrisonerHood(player)
	End Sub

	' Token: 0x06000746 RID: 1862 RVA: 0x00056318 File Offset: 0x00054518
	Private Sub EquipPrisonerHood(placingPlayer As Global.BasePlayer)
		If placingPlayer Is Nothing Then
			Return
		End If
		If Me.IsDead() OrElse Not Me.IsRestrained Then
			Return
		End If
		If Me.inventory Is Nothing Then
			Return
		End If
		If Me.inventory.GetEquippedPrisonerHoodItem() IsNot Nothing Then
			Return
		End If
		Dim usableHoodItem As Global.Item = placingPlayer.inventory.GetUsableHoodItem()
		If usableHoodItem Is Nothing Then
			Return
		End If
		Me.inventory.SetLockedByRestraint(False)
		If Not usableHoodItem.MoveToContainer(Me.inventory.containerBelt, -1, True, False, Nothing, True) Then
			Dim slot As Global.Item = Me.inventory.containerBelt.GetSlot(0)
			If slot IsNot Nothing Then
				Dim item As Global.Item = slot
				Dim restraintItem As Handcuffs = Me.Belt.GetRestraintItem()
				If item Is If((restraintItem IsNot Nothing), restraintItem.GetItem(), Nothing) Then
					slot = Me.inventory.containerBelt.GetSlot(1)
				End If
			End If
			If slot IsNot Nothing Then
				If Not slot.MoveToContainer(Me.inventory.containerMain, -1, True, False, Nothing, True) Then
					slot.DropAndTossUpwards(MyBase.transform.position, 2F)
				End If
				usableHoodItem.MoveToContainer(Me.inventory.containerBelt, -1, True, False, Nothing, True)
			End If
		End If
		Me.inventory.SetLockedByRestraint(True)
	End Sub

	' Token: 0x06000747 RID: 1863 RVA: 0x0005642C File Offset: 0x0005462C
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.CallsPerSecond(5UL)>
	<Global.BaseEntity.RPC_Server.MaxDistance(3F)>
	<Global.BaseEntity.RPC_Server.IsVisible(3F)>
	Private Sub RPC_ReqForceMountNearest(rpc As Global.BaseEntity.RPCMessage)
		Dim player As Global.BasePlayer = rpc.player
		If player Is Nothing Then
			Return
		End If
		Me.ForceRestrainedMountNearest(player)
	End Sub

	' Token: 0x06000748 RID: 1864 RVA: 0x00056454 File Offset: 0x00054654
	Private Sub ForceRestrainedMountNearest(forcingPlayer As Global.BasePlayer)
		If forcingPlayer Is Nothing Then
			Return
		End If
		If Me.isMounted Then
			Return
		End If
		If Not Me.IsRestrained OrElse Me.IsDead() OrElse Me.IsSleeping() OrElse Me.IsWounded() Then
			Return
		End If
		Dim list As List(Of BaseMountable) = Facepunch.Pool.GetList(Of BaseMountable)()
		Global.Vis.Entities(Of BaseMountable)(MyBase.transform.position, 2F, list, -1, QueryTriggerInteraction.Collide)
		list.Sort(Function(a As BaseMountable, b As BaseMountable) (MyBase.transform.position - a.transform.position).sqrMagnitude.CompareTo((MyBase.transform.position - b.transform.position).sqrMagnitude))
		For Each baseMountable As BaseMountable In list
			If Not baseMountable.isClient AndAlso baseMountable.AllowForceMountWhenRestrained AndAlso Not(baseMountable.VehicleParent() IsNot Nothing) AndAlso baseMountable.DirectlyMountable() AndAlso baseMountable.Distance(Me.eyes.position) <= 3F AndAlso GamePhysics.LineOfSight(Me.eyes.center, Me.eyes.position, 1218519041, Nothing) AndAlso (baseMountable.IsVisible(Me.eyes.HeadRay(), 1218519041, 3F) OrElse baseMountable.IsVisible(Me.eyes.position, 3F)) Then
				Dim flag As Boolean = False
				Dim modularCar As Global.ModularCar = TryCast(baseMountable, Global.ModularCar)
				If modularCar IsNot Nothing AndAlso modularCar.CarLock.HasALock Then
					flag = Not modularCar.CarLock.HasLockPermission(Me)
					If modularCar.CarLock.HasLockPermission(forcingPlayer) Then
						modularCar.CarLock.TryAddPlayer(Me.userID)
					End If
				End If
				baseMountable.AttemptMount(Me, True)
				If modularCar IsNot Nothing AndAlso modularCar.CarLock.HasALock AndAlso flag Then
					modularCar.CarLock.TryRemovePlayer(Me.userID)
				End If
				If Me.isMounted Then
					Exit For
				End If
			End If
		Next
		Facepunch.Pool.FreeList(Of BaseMountable)(list)
	End Sub

	' Token: 0x06000749 RID: 1865 RVA: 0x00056664 File Offset: 0x00054864
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.CallsPerSecond(5UL)>
	<Global.BaseEntity.RPC_Server.MaxDistance(3F)>
	<Global.BaseEntity.RPC_Server.IsVisible(3F)>
	Private Sub RPC_ReqForceSwapSeat(rpc As Global.BaseEntity.RPCMessage)
		If Not Me.isMounted Then
			Return
		End If
		If Not Me.IsRestrained OrElse Me.IsDead() OrElse Me.IsSleeping() OrElse Me.IsWounded() Then
			Return
		End If
		If rpc.player Is Nothing Then
			Return
		End If
		Dim player As Global.BasePlayer = rpc.player
		Dim baseMountable As BaseMountable = Me.GetMounted()
		If baseMountable Is Nothing Then
			Return
		End If
		Dim baseVehicle As Global.BaseVehicle = baseMountable.GetComponent(Of Global.BaseVehicle)()
		If baseVehicle Is Nothing Then
			baseVehicle = baseMountable.VehicleParent()
		End If
		If baseVehicle Is Nothing Then
			Return
		End If
		Dim flag As Boolean = False
		Dim modularCar As Global.ModularCar = TryCast(baseVehicle, Global.ModularCar)
		If modularCar IsNot Nothing AndAlso modularCar.CarLock.HasALock Then
			flag = Not modularCar.CarLock.HasLockPermission(Me)
			If modularCar.CarLock.HasLockPermission(player) Then
				modularCar.CarLock.TryAddPlayer(Me.userID)
			End If
		End If
		baseVehicle.SwapSeats(Me, 0, True)
		If modularCar IsNot Nothing AndAlso modularCar.CarLock.HasALock AndAlso flag Then
			modularCar.CarLock.TryRemovePlayer(Me.userID)
		End If
	End Sub

	' Token: 0x0600074A RID: 1866 RVA: 0x0005677C File Offset: 0x0005497C
	Public Function CanMoveFrom(player As Global.BasePlayer, item As Global.Item) As Boolean Implements PlayerInventory.ICanMoveFrom.CanMoveFrom
		If Me.IsRestrainedOrSurrendering Then
			Dim itemContainer As Global.ItemContainer = If((item IsNot Nothing), item.parent, Nothing)
			If itemContainer Is Nothing Then
				Return True
			End If
			If itemContainer.IsLocked() Then
				Return False
			End If
			If itemContainer Is Me.inventory.containerBelt AndAlso item.IsOn() AndAlso item.info.GetComponent(Of ItemModRestraint)() IsNot Nothing Then
				Return False
			End If
		End If
		Return True
	End Function

	' Token: 0x170000D8 RID: 216
	' (get) Token: 0x0600074B RID: 1867 RVA: 0x000567D9 File Offset: 0x000549D9
	Public ReadOnly Property hasPreviousLife As Boolean
		Get
			Return Me.previousLifeStory IsNot Nothing
		End Get
	End Property

	' Token: 0x170000D9 RID: 217
	' (get) Token: 0x0600074C RID: 1868 RVA: 0x000567E4 File Offset: 0x000549E4
	' (set) Token: 0x0600074D RID: 1869 RVA: 0x000567EC File Offset: 0x000549EC
	Public Property currentTimeCategory As Integer

	' Token: 0x0600074E RID: 1870 RVA: 0x000567F5 File Offset: 0x000549F5
	Friend Sub LifeStoryStart()
		If Me.lifeStory IsNot Nothing Then
			Me.lifeStory = Nothing
		End If
		Me.lifeStory = New PlayerLifeStory() With { .ShouldPool = False }
		Me.lifeStory.timeBorn = CUInt(Epoch.Current)
		Me.hasSentPresenceState = False
	End Sub

	' Token: 0x0600074F RID: 1871 RVA: 0x0005682F File Offset: 0x00054A2F
	Friend Sub LifeStoryEnd()
		SingletonComponent(Of ServerMgr).Instance.persistance.AddLifeStory(Me.userID, Me.lifeStory)
		Me.previousLifeStory = Me.lifeStory
		Me.lifeStory = Nothing
	End Sub

	' Token: 0x06000750 RID: 1872 RVA: 0x00056864 File Offset: 0x00054A64
	Friend Sub LifeStoryUpdate(deltaTime As Single, moveSpeed As Single)
		If Me.lifeStory Is Nothing Then
			Return
		End If
		Me.lifeStory.secondsAlive += deltaTime
		Me.nextTimeCategoryUpdate -= deltaTime * If((moveSpeed > 0.1F), 1F, 0.25F)
		If Me.nextTimeCategoryUpdate <= 0F AndAlso Not Me.waitingForLifeStoryUpdate Then
			Me.nextTimeCategoryUpdate = 7F + 7F * UnityEngine.Random.Range(0.2F, 1F)
			Me.waitingForLifeStoryUpdate = True
			Global.BasePlayer.lifeStoryQueue.Add(Me)
		End If
		If Me.LifeStoryInWilderness Then
			Me.lifeStory.secondsWilderness += deltaTime
		End If
		If Me.LifeStoryInMonument Then
			Me.lifeStory.secondsInMonument += deltaTime
		End If
		If Me.LifeStoryInBase Then
			Me.lifeStory.secondsInBase += deltaTime
		End If
		If Me.LifeStoryFlying Then
			Me.lifeStory.secondsFlying += deltaTime
		End If
		If Me.LifeStoryBoating Then
			Me.lifeStory.secondsBoating += deltaTime
		End If
		If Me.LifeStorySwimming Then
			Me.lifeStory.secondsSwimming += deltaTime
		End If
		If Me.LifeStoryDriving Then
			Me.lifeStory.secondsDriving += deltaTime
		End If
		If Me.IsSleeping() Then
			Me.lifeStory.secondsSleeping += deltaTime
			Return
		End If
		If Me.IsRunning() Then
			Me.lifeStory.metersRun += moveSpeed * deltaTime
			Return
		End If
		Me.lifeStory.metersWalked += moveSpeed * deltaTime
	End Sub

	' Token: 0x06000751 RID: 1873 RVA: 0x00056A04 File Offset: 0x00054C04
	Public Sub UpdateTimeCategory()
		Using TimeWarning.[New]("UpdateTimeCategory", 0)
			Me.waitingForLifeStoryUpdate = False
			Dim currentTimeCategory As Integer = Me.currentTimeCategory
			Me.currentTimeCategory = 1
			If Me.IsBuildingAuthed() Then
				Me.currentTimeCategory = 4
			End If
			Dim position As Vector3 = MyBase.transform.position
			If TerrainMeta.TopologyMap IsNot Nothing AndAlso (TerrainMeta.TopologyMap.GetTopology(position) And 1024) <> 0 Then
				For Each monumentInfo As MonumentInfo In TerrainMeta.Path.Monuments
					If monumentInfo.shouldDisplayOnMap AndAlso monumentInfo.IsInBounds(position) Then
						Me.currentTimeCategory = 2
						Exit For
					End If
				Next
			End If
			If Me.IsSwimming() Then
				Me.currentTimeCategory = Me.currentTimeCategory Or 32
			End If
			If Me.isMounted Then
				Dim baseMountable As BaseMountable = Me.GetMounted()
				If baseMountable.mountTimeStatType = BaseMountable.MountStatType.Boating Then
					Me.currentTimeCategory = Me.currentTimeCategory Or 16
				ElseIf baseMountable.mountTimeStatType = BaseMountable.MountStatType.Flying Then
					Me.currentTimeCategory = Me.currentTimeCategory Or 8
				ElseIf baseMountable.mountTimeStatType = BaseMountable.MountStatType.Driving Then
					Me.currentTimeCategory = Me.currentTimeCategory Or 64
				End If
			ElseIf MyBase.HasParent() Then
				Dim baseMountable2 As BaseMountable = TryCast(MyBase.GetParentEntity(), BaseMountable)
				If baseMountable2 IsNot Nothing Then
					If baseMountable2.mountTimeStatType = BaseMountable.MountStatType.Boating Then
						Me.currentTimeCategory = Me.currentTimeCategory Or 16
					ElseIf baseMountable2.mountTimeStatType = BaseMountable.MountStatType.Flying Then
						Me.currentTimeCategory = Me.currentTimeCategory Or 8
					ElseIf baseMountable2.mountTimeStatType = BaseMountable.MountStatType.Driving Then
						Me.currentTimeCategory = Me.currentTimeCategory Or 64
					End If
				End If
			End If
			If currentTimeCategory <> Me.currentTimeCategory OrElse Not Me.hasSentPresenceState Then
				Me.LifeStoryInWilderness = ((1 And Me.currentTimeCategory) <> 0)
				Me.LifeStoryInMonument = ((2 And Me.currentTimeCategory) <> 0)
				Me.LifeStoryInBase = ((4 And Me.currentTimeCategory) <> 0)
				Me.LifeStoryFlying = ((8 And Me.currentTimeCategory) <> 0)
				Me.LifeStoryBoating = ((16 And Me.currentTimeCategory) <> 0)
				Me.LifeStorySwimming = ((32 And Me.currentTimeCategory) <> 0)
				Me.LifeStoryDriving = ((64 And Me.currentTimeCategory) <> 0)
				MyBase.ClientRPC(Of Integer)(RpcTarget.Player("UpdateRichPresenceState", Me), Me.currentTimeCategory)
				Me.hasSentPresenceState = True
			End If
		End Using
	End Sub

	' Token: 0x06000752 RID: 1874 RVA: 0x00056C90 File Offset: 0x00054E90
	Public Sub LifeStoryShotFired(withWeapon As Global.BaseEntity)
		If Me.lifeStory Is Nothing Then
			Return
		End If
		If Me.lifeStory.weaponStats Is Nothing Then
			Me.lifeStory.weaponStats = Facepunch.Pool.GetList(Of PlayerLifeStory.WeaponStats)()
		End If
		For Each weaponStats As PlayerLifeStory.WeaponStats In Me.lifeStory.weaponStats
			If weaponStats.weaponName = withWeapon.ShortPrefabName Then
				weaponStats.shotsFired += 1UL
				Return
			End If
		Next
		Dim weaponStats2 As PlayerLifeStory.WeaponStats = Facepunch.Pool.[Get](Of PlayerLifeStory.WeaponStats)()
		weaponStats2.weaponName = withWeapon.ShortPrefabName
		weaponStats2.shotsFired += 1UL
		Me.lifeStory.weaponStats.Add(weaponStats2)
	End Sub

	' Token: 0x06000753 RID: 1875 RVA: 0x00056D60 File Offset: 0x00054F60
	Public Sub LifeStoryShotHit(withWeapon As Global.BaseEntity)
		If Me.lifeStory Is Nothing OrElse withWeapon Is Nothing Then
			Return
		End If
		If Me.lifeStory.weaponStats Is Nothing Then
			Me.lifeStory.weaponStats = Facepunch.Pool.GetList(Of PlayerLifeStory.WeaponStats)()
		End If
		For Each weaponStats As PlayerLifeStory.WeaponStats In Me.lifeStory.weaponStats
			If weaponStats.weaponName = withWeapon.ShortPrefabName Then
				weaponStats.shotsHit += 1UL
				Return
			End If
		Next
		Dim weaponStats2 As PlayerLifeStory.WeaponStats = Facepunch.Pool.[Get](Of PlayerLifeStory.WeaponStats)()
		weaponStats2.weaponName = withWeapon.ShortPrefabName
		weaponStats2.shotsHit += 1UL
		Me.lifeStory.weaponStats.Add(weaponStats2)
	End Sub

	' Token: 0x06000754 RID: 1876 RVA: 0x00056E38 File Offset: 0x00055038
	Public Sub LifeStoryKill(killed As BaseCombatEntity)
		If Me.lifeStory Is Nothing Then
			Return
		End If
		If TypeOf killed Is ScientistNPC Then
			Me.lifeStory.killedScientists += 1
			Return
		End If
		If TypeOf killed Is Global.BasePlayer Then
			Me.lifeStory.killedPlayers += 1
			Return
		End If
		If TypeOf killed Is BaseAnimalNPC Then
			Me.lifeStory.killedAnimals += 1
		End If
	End Sub

	' Token: 0x06000755 RID: 1877 RVA: 0x00056EA4 File Offset: 0x000550A4
	Public Sub LifeStoryGenericStat(key As String, value As Integer)
		If Me.lifeStory Is Nothing Then
			Return
		End If
		If Me.lifeStory.genericStats Is Nothing Then
			Me.lifeStory.genericStats = Facepunch.Pool.GetList(Of PlayerLifeStory.GenericStat)()
		End If
		For Each genericStat As PlayerLifeStory.GenericStat In Me.lifeStory.genericStats
			If genericStat.key = key Then
				genericStat.value += value
				Return
			End If
		Next
		Dim genericStat2 As PlayerLifeStory.GenericStat = Facepunch.Pool.[Get](Of PlayerLifeStory.GenericStat)()
		genericStat2.key = key
		genericStat2.value = value
		Me.lifeStory.genericStats.Add(genericStat2)
	End Sub

	' Token: 0x06000756 RID: 1878 RVA: 0x00056F60 File Offset: 0x00055160
	Public Sub LifeStoryHurt(amount As Single)
		If Me.lifeStory Is Nothing Then
			Return
		End If
		Me.lifeStory.totalDamageTaken += amount
	End Sub

	' Token: 0x06000757 RID: 1879 RVA: 0x00056F7E File Offset: 0x0005517E
	Public Sub LifeStoryHeal(amount As Single)
		If Me.lifeStory Is Nothing Then
			Return
		End If
		Me.lifeStory.totalHealing += amount
	End Sub

	' Token: 0x06000758 RID: 1880 RVA: 0x00056F9C File Offset: 0x0005519C
	Public Sub SetOverrideDeathBlow(info As PlayerLifeStory.DeathInfo)
		Me.cachedOverrideDeathInfo = info
	End Sub

	' Token: 0x06000759 RID: 1881 RVA: 0x00056FA8 File Offset: 0x000551A8
	Friend Sub LifeStoryLogDeath(deathBlow As HitInfo, lastDamage As DamageType)
		If Me.lifeStory Is Nothing Then
			Return
		End If
		Me.lifeStory.timeDied = CUInt(Epoch.Current)
		Dim deathInfo As PlayerLifeStory.DeathInfo = If(Me.cachedOverrideDeathInfo, Facepunch.Pool.[Get](Of PlayerLifeStory.DeathInfo)())
		deathInfo.lastDamageType = CInt(lastDamage)
		Me.cachedOverrideDeathInfo = Nothing
		If deathBlow IsNot Nothing Then
			If deathBlow.Initiator IsNot Nothing Then
				deathBlow.Initiator.AttackerInfo(deathInfo)
				deathInfo.attackerDistance = MyBase.Distance(deathBlow.Initiator)
			End If
			If deathBlow.WeaponPrefab IsNot Nothing Then
				deathInfo.inflictorName = deathBlow.WeaponPrefab.ShortPrefabName
			End If
			If deathBlow.HitBone > 0UI Then
				deathInfo.hitBone = StringPool.[Get](deathBlow.HitBone)
			Else
				deathInfo.hitBone = ""
			End If
		ElseIf MyBase.SecondsSinceAttacked <= 60F AndAlso Me.lastAttacker IsNot Nothing Then
			Me.lastAttacker.AttackerInfo(deathInfo)
		End If
		Me.lifeStory.deathInfo = deathInfo
	End Sub

	' Token: 0x170000DA RID: 218
	' (get) Token: 0x0600075A RID: 1882 RVA: 0x00057096 File Offset: 0x00055296
	' (set) Token: 0x0600075B RID: 1883 RVA: 0x0005709E File Offset: 0x0005529E
	Public Property IsBeingSpectated As Boolean

	' Token: 0x0600075C RID: 1884 RVA: 0x000570A7 File Offset: 0x000552A7
	Public Sub SetSpectateTeamInfo(state As Boolean)
		Me.IsSpectatingTeamInfo = state
	End Sub

	' Token: 0x0600075D RID: 1885 RVA: 0x000570B0 File Offset: 0x000552B0
	Private Sub Tick_Spectator()
		Dim num As Integer = 0
		If Me.serverInput.WasJustPressed(BUTTON.JUMP) Then
			num += 1
		End If
		If Me.serverInput.WasJustPressed(BUTTON.DUCK) Then
			num -= 1
		End If
		If num <> 0 Then
			Me.SpectateOffset += num
			Using TimeWarning.[New]("UpdateSpectateTarget", 0)
				Me.UpdateSpectateTarget(Me.spectateFilter)
			End Using
		End If
		If Me.lastSpectateTeamInfoUpdate > 0.5F AndAlso Me.IsSpectatingTeamInfo Then
			Me.lastSpectateTeamInfoUpdate = 0F
			Dim spectateTeamInfo As SpectateTeamInfo = Facepunch.Pool.[Get](Of SpectateTeamInfo)()
			spectateTeamInfo.teams = Facepunch.Pool.GetList(Of SpectateTeam)()
			spectateTeamInfo.teams.Clear()
			For Each keyValuePair As KeyValuePair(Of ULong, Global.RelationshipManager.PlayerTeam) In Global.RelationshipManager.ServerInstance.teams
				Dim spectateTeam As SpectateTeam = Facepunch.Pool.[Get](Of SpectateTeam)()
				spectateTeam.teamId = keyValuePair.Key
				spectateTeam.teamMembers = Facepunch.Pool.GetList(Of PlayerTeam.TeamMember)()
				spectateTeam.teamMembers.Clear()
				For Each playerID As ULong In keyValuePair.Value.members
					Dim teamMember As PlayerTeam.TeamMember = Facepunch.Pool.[Get](Of PlayerTeam.TeamMember)()
					teamMember.userID = playerID
					Dim basePlayer As Global.BasePlayer = Global.RelationshipManager.FindByID(playerID)
					teamMember.displayName = If((basePlayer IsNot Nothing), basePlayer.displayName, (If(SingletonComponent(Of ServerMgr).Instance.persistance.GetPlayerName(playerID), "DEAD")))
					teamMember.healthFraction = If((basePlayer IsNot Nothing AndAlso basePlayer.IsAlive()), basePlayer.healthFraction, 0F)
					teamMember.position = If((basePlayer IsNot Nothing), basePlayer.transform.position, Vector3.zero)
					teamMember.online = (basePlayer IsNot Nothing AndAlso Not basePlayer.IsSleeping())
					teamMember.wounded = (basePlayer IsNot Nothing AndAlso basePlayer.IsWounded())
					spectateTeam.teamMembers.Add(teamMember)
				Next
				spectateTeamInfo.teams.Add(spectateTeam)
			Next
			MyBase.ClientRPC(Of SpectateTeamInfo)(RpcTarget.Player("ReceiveSpectateTeamInfo", Me), spectateTeamInfo)
		End If
	End Sub

	' Token: 0x0600075E RID: 1886 RVA: 0x00057358 File Offset: 0x00055558
	Public Sub UpdateSpectateTarget(strName As String)
		Me.spectateFilter = strName
		Dim source As IEnumerable(Of Global.BaseEntity)
		If Me.spectateFilter.StartsWith("@") Then
			Dim filter As String = Me.spectateFilter.Substring(1)
			source = Global.BaseNetworkable.serverEntities.Where(Function(x As Global.BaseNetworkable) x.name.Contains(filter, CompareOptions.IgnoreCase)).Where(Function(x As Global.BaseNetworkable) x IsNot Me).Cast()
		Else
			Dim source2 As IEnumerable(Of Global.BasePlayer) = Global.BasePlayer.activePlayerList
			Dim <>9__585_ As Func(Of Global.BasePlayer, Boolean) = Global.BasePlayer.<>c.<>9__585_2
			Dim predicate As Func(Of Global.BasePlayer, Boolean) = <>9__585_
			If <>9__585_ Is Nothing Then
				Dim func As Func(Of Global.BasePlayer, Boolean) = Function(x As Global.BasePlayer) Not x.IsSpectating() AndAlso Not x.IsDead() AndAlso Not x.IsSleeping()
				predicate = func
				Global.BasePlayer.<>c.<>9__585_2 = func
			End If
			Dim enumerable As IEnumerable(Of Global.BasePlayer) = source2.Where(predicate)
			If strName.Length > 0 Then
				enumerable = enumerable.Where(Function(x As Global.BasePlayer) x.displayName.Contains(Me.spectateFilter, CompareOptions.IgnoreCase) OrElse x.UserIDString.Contains(Me.spectateFilter)).Where(Function(x As Global.BasePlayer) x IsNot Me)
			End If
			Dim source3 As IEnumerable(Of Global.BasePlayer) = enumerable
			Dim <>9__585_2 As Func(Of Global.BasePlayer, String) = Global.BasePlayer.<>c.<>9__585_5
			Dim keySelector As Func(Of Global.BasePlayer, String) = <>9__585_2
			If <>9__585_2 Is Nothing Then
				Dim func2 As Func(Of Global.BasePlayer, String) = Function(x As Global.BasePlayer) x.displayName
				keySelector = func2
				Global.BasePlayer.<>c.<>9__585_5 = func2
			End If
			enumerable = source3.OrderBy(keySelector)
			source = enumerable.Cast()
		End If
		Dim array As Global.BaseEntity() = source.ToArray()
		If array.Length = 0 Then
			Me.ChatMessage("No valid spectate targets!")
			Return
		End If
		Dim baseEntity As Global.BaseEntity = array(Me.SpectateOffset Mod array.Length)
		If baseEntity IsNot Nothing Then
			Me.SpectatePlayer(baseEntity)
		End If
	End Sub

	' Token: 0x0600075F RID: 1887 RVA: 0x00057488 File Offset: 0x00055688
	Public Sub UpdateSpectateTarget(id As ULong)
		For Each basePlayer As Global.BasePlayer In Global.BasePlayer.activePlayerList
			If basePlayer IsNot Nothing AndAlso basePlayer.userID = id Then
				Me.spectateFilter = String.Empty
				Me.SpectatePlayer(basePlayer)
				Exit For
			End If
		Next
	End Sub

	' Token: 0x06000760 RID: 1888 RVA: 0x00057500 File Offset: 0x00055700
	Private Sub SpectatePlayer(target As Global.BaseEntity)
		If TypeOf target Is Global.BasePlayer Then
			Me.ChatMessage("Spectating: " + TryCast(target, Global.BasePlayer).displayName)
		Else
			Me.ChatMessage("Spectating: " + target.ToString())
		End If
		Using TimeWarning.[New]("SendEntitySnapshot", 0)
			Me.SendEntitySnapshot(target)
		End Using
		MyBase.gameObject.Identity()
		Using TimeWarning.[New]("SetParent", 0)
			MyBase.SetParent(target, False, False)
		End Using
	End Sub

	' Token: 0x06000761 RID: 1889 RVA: 0x000575B0 File Offset: 0x000557B0
	Public Sub StartSpectating()
		If Me.IsSpectating() Then
			Return
		End If
		Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.Spectating, True)
		MyBase.gameObject.SetLayerRecursive(10)
		MyBase.CancelInvoke(AddressOf Me.InventoryUpdate)
		Me.ChatMessage("Becoming Spectator")
		Me.UpdateSpectateTarget(Me.spectateFilter)
	End Sub

	' Token: 0x06000762 RID: 1890 RVA: 0x00057605 File Offset: 0x00055805
	Public Sub StopSpectating()
		If Not Me.IsSpectating() Then
			Return
		End If
		MyBase.SetParent(Nothing, False, False)
		Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.Spectating, False)
		MyBase.gameObject.SetLayerRecursive(17)
	End Sub

	' Token: 0x06000763 RID: 1891 RVA: 0x0005762F File Offset: 0x0005582F
	Public Sub Teleport(player As Global.BasePlayer)
		Me.Teleport(player.transform.position)
	End Sub

	' Token: 0x06000764 RID: 1892 RVA: 0x00057644 File Offset: 0x00055844
	Public Sub Teleport(strName As String, playersOnly As Boolean)
		Dim array As Global.BaseEntity() = Global.BaseEntity.Util.FindTargets(strName, playersOnly)
		If array Is Nothing OrElse array.Length = 0 Then
			Return
		End If
		Dim baseEntity As Global.BaseEntity = array(UnityEngine.Random.Range(0, array.Length))
		Me.Teleport(baseEntity.transform.position)
	End Sub

	' Token: 0x06000765 RID: 1893 RVA: 0x0005767E File Offset: 0x0005587E
	Public Sub Teleport(position As Vector3)
		Me.MovePosition(position)
		MyBase.ClientRPC(Of Vector3)(RpcTarget.Player("ForcePositionTo", Me), position)
	End Sub

	' Token: 0x06000766 RID: 1894 RVA: 0x00057699 File Offset: 0x00055899
	Public Sub CopyRotation(player As Global.BasePlayer)
		Me.viewAngles = player.viewAngles
		MyBase.SendNetworkUpdate_Position()
	End Sub

	' Token: 0x06000767 RID: 1895 RVA: 0x000576AD File Offset: 0x000558AD
	Protected Overrides Sub OnChildAdded(child As Global.BaseEntity)
		MyBase.OnChildAdded(child)
		If TypeOf child Is Global.BasePlayer Then
			Me.IsBeingSpectated = True
		End If
	End Sub

	' Token: 0x06000768 RID: 1896 RVA: 0x000576C8 File Offset: 0x000558C8
	Protected Overrides Sub OnChildRemoved(child As Global.BaseEntity)
		MyBase.OnChildRemoved(child)
		If TypeOf child Is Global.BasePlayer Then
			Me.IsBeingSpectated = False
			Using enumerator As List(Of Global.BaseEntity).Enumerator = Me.children.GetEnumerator()
				While enumerator.MoveNext()
					If TypeOf enumerator.Current Is Global.BasePlayer Then
						Me.IsBeingSpectated = True
					End If
				End While
			End Using
		End If
	End Sub

	' Token: 0x06000769 RID: 1897 RVA: 0x00057738 File Offset: 0x00055938
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.FromOwner()>
	<Global.BaseEntity.RPC_Server.CallsPerSecond(10UL)>
	Private Sub UpdateSpectatePositionFromDebugCamera(msg As Global.BaseEntity.RPCMessage)
		If Not Me.IsSpectating() OrElse Not ConVar.[Global].updateNetworkPositionWithDebugCameraWhileSpectating Then
			Return
		End If
		Dim position As Vector3 = msg.read.Vector3()
		MyBase.transform.position = position
		MyBase.SetParent(Nothing, False, False)
	End Sub

	' Token: 0x0600076A RID: 1898 RVA: 0x00057776 File Offset: 0x00055976
	<Global.BaseEntity.RPC_Server()>
	Private Sub NotifyDebugCameraEnded(msg As Global.BaseEntity.RPCMessage)
		If Not Me.IsSpectating() OrElse Not ConVar.[Global].updateNetworkPositionWithDebugCameraWhileSpectating Then
			Return
		End If
		Me.UpdateSpectateTarget(Me.spectateFilter)
	End Sub

	' Token: 0x0600076B RID: 1899 RVA: 0x00057794 File Offset: 0x00055994
	Public Sub AddNeabyStash(newStash As StashContainer)
		If newStash Is Nothing Then
			Return
		End If
		Using enumerator As List(Of Global.BasePlayer.NearbyStash).Enumerator = Me.nearbyStashes.GetEnumerator()
			While enumerator.MoveNext()
				If enumerator.Current.Entity Is newStash Then
					Return
				End If
			End While
		End Using
		If Me.nearbyStashes.Count = 0 Then
			MyBase.InvokeRepeating(AddressOf Me.CheckStashRevealInvoke, 0F, StashContainer.PlayerDetectionTickRate)
		End If
		Me.nearbyStashes.Add(New Global.BasePlayer.NearbyStash(newStash))
	End Sub

	' Token: 0x0600076C RID: 1900 RVA: 0x00057834 File Offset: 0x00055A34
	Public Sub RemoveNearbyStash(stash As StashContainer)
		For i As Integer = 0 To Me.nearbyStashes.Count - 1
			If Not(Me.nearbyStashes(i).Entity IsNot stash) Then
				Me.nearbyStashes.RemoveAt(i)
				Exit For
			End If
		Next
		If Me.nearbyStashes.Count = 0 Then
			MyBase.CancelInvoke(AddressOf Me.CheckStashRevealInvoke)
		End If
	End Sub

	' Token: 0x0600076D RID: 1901 RVA: 0x000578A0 File Offset: 0x00055AA0
	Private Sub CheckStashRevealInvoke()
		For i As Integer = 0 To Me.nearbyStashes.Count - 1
			Dim nearbyStash As Global.BasePlayer.NearbyStash = Me.nearbyStashes(i)
			If nearbyStash.Entity Is Nothing OrElse nearbyStash.Entity.IsDestroyed Then
				Me.nearbyStashes.RemoveAt(i)
			ElseIf nearbyStash.Entity.IsHidden() AndAlso nearbyStash.Entity.PlayerInRange(Me) Then
				nearbyStash.LookingAtTime += StashContainer.PlayerDetectionTickRate
				If nearbyStash.LookingAtTime >= nearbyStash.Entity.uncoverTime Then
					nearbyStash.Entity.SetHidden(False)
					Analytics.Azure.OnStashRevealed(Me, nearbyStash.Entity)
				End If
			Else
				nearbyStash.LookingAtTime = 0F
			End If
		Next
	End Sub

	' Token: 0x0600076E RID: 1902 RVA: 0x00057964 File Offset: 0x00055B64
	Public Overrides Function GetThreatLevel() As Single
		Me.EnsureUpdated()
		Return Me.cachedThreatLevel
	End Function

	' Token: 0x0600076F RID: 1903 RVA: 0x00057974 File Offset: 0x00055B74
	Public Sub EnsureUpdated()
		If UnityEngine.Time.realtimeSinceStartup - Me.lastUpdateTime < 30F Then
			Return
		End If
		Me.lastUpdateTime = UnityEngine.Time.realtimeSinceStartup
		Me.cachedThreatLevel = 0F
		If Not Me.IsSleeping() Then
			If Me.inventory.containerWear.itemList.Count > 2 Then
				Me.cachedThreatLevel += 1F
			End If
			For Each item As Global.Item In Me.inventory.containerBelt.itemList
				Dim heldEntity As Global.BaseEntity = item.GetHeldEntity()
				If heldEntity AndAlso TypeOf heldEntity Is Global.BaseProjectile AndAlso Not(TypeOf heldEntity Is BowWeapon) Then
					Me.cachedThreatLevel += 2F
					Exit For
				End If
			Next
		End If
	End Sub

	' Token: 0x06000770 RID: 1904 RVA: 0x00057A5C File Offset: 0x00055C5C
	Public Overrides Function IsHostile() As Boolean
		Return Me.State.unHostileTimestamp > TimeEx.currentTimestamp
	End Function

	' Token: 0x06000771 RID: 1905 RVA: 0x00057A70 File Offset: 0x00055C70
	Public Overridable Function GetHostileDuration() As Single
		Return Mathf.Clamp(CSng((Me.State.unHostileTimestamp - TimeEx.currentTimestamp)), 0F, Single.PositiveInfinity)
	End Function

	' Token: 0x06000772 RID: 1906 RVA: 0x00057A94 File Offset: 0x00055C94
	Public Overrides Sub MarkHostileFor(Optional duration As Single = 60F)
		Dim currentTimestamp As Double = TimeEx.currentTimestamp
		Dim val As Double = currentTimestamp + CDbl(duration)
		Me.State.unHostileTimestamp = Math.Max(Me.State.unHostileTimestamp, val)
		Me.DirtyPlayerState()
		Dim num As Double = Math.Max(Me.State.unHostileTimestamp - currentTimestamp, 0.0)
		MyBase.ClientRPC(Of Single)(RpcTarget.Player("SetHostileLength", Me), CSng(num))
	End Sub

	' Token: 0x06000773 RID: 1907 RVA: 0x00057B00 File Offset: 0x00055D00
	Public Sub MarkWeaponDrawnDuration(newDuration As Single)
		Dim num As Single = Me.weaponDrawnDuration
		Me.weaponDrawnDuration = newDuration
		If CSng(Mathf.FloorToInt(newDuration)) <> num Then
			MyBase.ClientRPC(Of Single)(RpcTarget.Player("SetWeaponDrawnDuration", Me), Me.weaponDrawnDuration)
		End If
	End Sub

	' Token: 0x06000774 RID: 1908 RVA: 0x00057B3C File Offset: 0x00055D3C
	Public Sub AddWeaponDrawnDuration(duration As Single)
		Me.MarkWeaponDrawnDuration(Me.weaponDrawnDuration + duration)
	End Sub

	' Token: 0x170000DB RID: 219
	' (get) Token: 0x06000775 RID: 1909 RVA: 0x00057B4C File Offset: 0x00055D4C
	' (set) Token: 0x06000776 RID: 1910 RVA: 0x00057B54 File Offset: 0x00055D54
	Public Property serverInput As InputState = New InputState()

	' Token: 0x170000DC RID: 220
	' (get) Token: 0x06000777 RID: 1911 RVA: 0x00057B5D File Offset: 0x00055D5D
	Public ReadOnly Property timeSinceLastTick As Single
		Get
			If Me.lastTickTime = 0F Then
				Return 0F
			End If
			Return UnityEngine.Time.time - Me.lastTickTime
		End Get
	End Property

	' Token: 0x170000DD RID: 221
	' (get) Token: 0x06000778 RID: 1912 RVA: 0x00057B7E File Offset: 0x00055D7E
	Public ReadOnly Property timeSinceLastStall As Single
		Get
			If Me.lastStallTime = 0F Then
				Return 60F
			End If
			Return UnityEngine.Time.time - Me.lastStallTime
		End Get
	End Property

	' Token: 0x170000DE RID: 222
	' (get) Token: 0x06000779 RID: 1913 RVA: 0x00057B9F File Offset: 0x00055D9F
	Public ReadOnly Property IdleTime As Single
		Get
			If Me.lastInputTime = 0F Then
				Return 0F
			End If
			Return UnityEngine.Time.time - Me.lastInputTime
		End Get
	End Property

	' Token: 0x170000DF RID: 223
	' (get) Token: 0x0600077A RID: 1914 RVA: 0x00057BC0 File Offset: 0x00055DC0
	Public ReadOnly Property isStalled As Boolean
		Get
			If Me.IsDead() OrElse Me.IsSleeping() Then
				Me.lastStallTime = 0F
				Return False
			End If
			If Me.timeSinceLastTick <> 0F AndAlso Me.timeSinceLastTick > ConVar.AntiHack.rpcstallthreshold Then
				Me.lastStallTime = UnityEngine.Time.time
				Return True
			End If
			Return False
		End Get
	End Property

	' Token: 0x170000E0 RID: 224
	' (get) Token: 0x0600077B RID: 1915 RVA: 0x00057C12 File Offset: 0x00055E12
	Public ReadOnly Property wasStalled As Boolean
		Get
			Return Me.isStalled OrElse Me.timeSinceLastStall < ConVar.AntiHack.rpcstallfade
		End Get
	End Property

	' Token: 0x0600077C RID: 1916 RVA: 0x00057C2C File Offset: 0x00055E2C
	Public Sub OnReceivedTick(stream As Stream)
		Using TimeWarning.[New]("OnReceiveTickFromStream", 0)
			Dim playerTick As PlayerTick = Nothing
			Using TimeWarning.[New]("PlayerTick.Deserialize", 0)
				playerTick = PlayerTick.Deserialize(stream, Me.lastReceivedTick, True)
			End Using
			Using TimeWarning.[New]("RecordPacket", 0)
				Me.net.connection.RecordPacket(15, playerTick)
			End Using
			Using TimeWarning.[New]("PlayerTick.Copy", 0)
				Me.lastReceivedTick = playerTick.Copy()
			End Using
			Using TimeWarning.[New]("OnReceiveTick", 0)
				Me.OnReceiveTick(playerTick, Me.wasStalled)
			End Using
			Me.lastTickTime = UnityEngine.Time.time
			playerTick.Dispose()
		End Using
	End Sub

	' Token: 0x0600077D RID: 1917 RVA: 0x00057D40 File Offset: 0x00055F40
	Public Sub OnReceivedVoice(data As Byte())
		Dim netWrite As NetWrite = Network.Net.sv.StartWrite()
		netWrite.PacketID(Message.Type.VoiceData)
		netWrite.EntityID(Me.net.ID)
		netWrite.BytesWithSize(data, False)
		Dim num As Single = 0F
		If Me.HasPlayerFlag(Global.BasePlayer.PlayerFlags.VoiceRangeBoost) Then
			num = Voice.voiceRangeBoostAmount
		End If
		netWrite.Send(New SendInfo(Global.BaseNetworkable.GetConnectionsWithin(MyBase.transform.position, 100F + num)) With { .priority = Priority.Immediate })
		If Me.activeTelephone IsNot Nothing Then
			Me.activeTelephone.OnReceivedVoiceFromUser(data)
		End If
	End Sub

	' Token: 0x0600077E RID: 1918 RVA: 0x00057DD7 File Offset: 0x00055FD7
	Public Sub ResetInputIdleTime()
		Me.lastInputTime = UnityEngine.Time.time
	End Sub

	' Token: 0x0600077F RID: 1919 RVA: 0x00057DE4 File Offset: 0x00055FE4
	Private Sub EACStateUpdate()
		If Me.IsReceivingSnapshot Then
			Return
		End If
		EACServer.LogPlayerTick(Me)
	End Sub

	' Token: 0x06000780 RID: 1920 RVA: 0x00057DF8 File Offset: 0x00055FF8
	Private Sub OnReceiveTick(msg As PlayerTick, wasPlayerStalled As Boolean)
		If msg.inputState IsNot Nothing Then
			Me.serverInput.Flip(msg.inputState)
		End If
		If Me.serverInput.current.buttons <> Me.serverInput.previous.buttons Then
			Me.ResetInputIdleTime()
		End If
		If Me.IsReceivingSnapshot Then
			Return
		End If
		If Me.IsSpectating() Then
			Using TimeWarning.[New]("Tick_Spectator", 0)
				Me.Tick_Spectator()
			End Using
			Return
		End If
		If Me.IsDead() Then
			Return
		End If
		If Me.IsSleeping() Then
			If Me.serverInput.WasJustPressed(BUTTON.FIRE_PRIMARY) OrElse Me.serverInput.WasJustPressed(BUTTON.FIRE_SECONDARY) OrElse Me.serverInput.WasJustPressed(BUTTON.JUMP) OrElse Me.serverInput.WasJustPressed(BUTTON.DUCK) Then
				Me.EndSleeping()
				MyBase.SendNetworkUpdateImmediate(False)
			End If
			Me.UpdateActiveItem(Nothing)
			Return
		End If
		If Me.IsRestrained AndAlso Me.restraintItemId IsNot Nothing AndAlso Me.restraintItemId IsNot Nothing Then
			Me.UpdateActiveItem(Me.restraintItemId.Value)
		Else
			Me.UpdateActiveItem(msg.activeItem)
		End If
		Me.UpdateModelStateFromTick(msg)
		If Me.IsIncapacitated() Then
			Return
		End If
		If Me.isMounted Then
			Me.GetMounted().PlayerServerInput(Me.serverInput, Me)
		End If
		Me.UpdatePositionFromTick(msg, wasPlayerStalled)
		Me.UpdateRotationFromTick(msg)
		Dim activeMission As Integer = Me.GetActiveMission()
		If activeMission >= 0 AndAlso activeMission < Me.missions.Count Then
			Dim missionInstance As BaseMission.MissionInstance = Me.missions(activeMission)
			If missionInstance.status = BaseMission.MissionStatus.Active AndAlso missionInstance.NeedsPlayerInput() Then
				Me.ProcessMissionEvent(BaseMission.MissionEventType.PLAYER_TICK, Me.net.ID, 0F)
			End If
		End If
		If Global.TutorialIsland.EnforceTrespassChecks AndAlso Not Me.IsAdmin AndAlso Not Me.IsNpc AndAlso Me.net IsNot Nothing AndAlso Me.net.group IsNot Nothing Then
			If Me.net.group.restricted Then
				Dim flag As Boolean = False
				If Not Me.IsInTutorial Then
					flag = True
				Else
					Dim currentTutorialIsland As Global.TutorialIsland = Me.GetCurrentTutorialIsland()
					If currentTutorialIsland Is Nothing OrElse currentTutorialIsland.net.group IsNot Me.net.group Then
						flag = True
					End If
				End If
				If Not flag Then
					Me.tutorialKickTime = 0F
					Return
				End If
				Me.tutorialKickTime += UnityEngine.Time.deltaTime
				If Me.tutorialKickTime > 3F Then
					Debug.LogWarning(String.Format("Killing player {0}/{1} as they are on a tutorial island that doesn't belong them", Me.displayName, Me.userID))
					MyBase.Hurt(999F)
					Me.tutorialKickTime = 0F
					Return
				End If
			ElseIf Me.IsInTutorial AndAlso Not Me.net.group.restricted Then
				Dim flag2 As Boolean = False
				Dim currentTutorialIsland2 As Global.TutorialIsland = Me.GetCurrentTutorialIsland()
				If currentTutorialIsland2 Is Nothing OrElse currentTutorialIsland2.net.group IsNot Me.net.group Then
					flag2 = True
				End If
				If flag2 Then
					Me.tutorialKickTime += UnityEngine.Time.deltaTime
					If Me.tutorialKickTime > 3F Then
						Debug.LogWarning(String.Format("Killing player {0}/{1} as they are no longer on a tutorial island and are marked as being in a tutorial", Me.displayName, Me.userID))
						MyBase.Hurt(999F)
						Me.tutorialKickTime = 0F
						Return
					End If
				Else
					Me.tutorialKickTime = 0F
				End If
			End If
		End If
	End Sub

	' Token: 0x06000781 RID: 1921 RVA: 0x0005816C File Offset: 0x0005636C
	Public Sub UpdateActiveItem(itemID As ItemId)
		Assert.IsTrue(MyBase.isServer, "Realm should be server!")
		If Me.svActiveItemID = itemID Then
			Return
		End If
		If Me.equippingBlocked Then
			itemID = Nothing
		End If
		Dim item As Global.Item = Me.inventory.containerBelt.FindItemByUID(itemID)
		If Me.IsItemHoldRestricted(item) Then
			itemID = Nothing
		End If
		Dim activeItem As Global.Item = Me.GetActiveItem()
		Me.svActiveItemID = Nothing
		If activeItem IsNot Nothing Then
			Dim heldEntity As Global.HeldEntity = TryCast(activeItem.GetHeldEntity(), Global.HeldEntity)
			If heldEntity IsNot Nothing Then
				heldEntity.SetHeld(False)
			End If
		End If
		Me.svActiveItemID = itemID
		MyBase.SendNetworkUpdate(Global.BasePlayer.NetworkQueue.Update)
		Dim activeItem2 As Global.Item = Me.GetActiveItem()
		If activeItem2 IsNot Nothing Then
			Dim heldEntity2 As Global.HeldEntity = TryCast(activeItem2.GetHeldEntity(), Global.HeldEntity)
			If heldEntity2 IsNot Nothing Then
				heldEntity2.SetHeld(True)
			End If
			Me.NotifyGesturesNewItemEquipped()
		End If
		Me.inventory.UpdatedVisibleHolsteredItems()
	End Sub

	' Token: 0x06000782 RID: 1922 RVA: 0x00058248 File Offset: 0x00056448
	Friend Sub UpdateModelStateFromTick(tick As PlayerTick)
		If tick.modelState Is Nothing Then
			Return
		End If
		If ModelState.Equal(Me.modelStateTick, tick.modelState) Then
			Return
		End If
		If Me.modelStateTick IsNot Nothing Then
			Me.modelStateTick.ResetToPool()
		End If
		Me.modelStateTick = tick.modelState
		tick.modelState = Nothing
		Me.tickNeedsFinalizing = True
	End Sub

	' Token: 0x06000783 RID: 1923 RVA: 0x000582A0 File Offset: 0x000564A0
	Friend Sub UpdatePositionFromTick(tick As PlayerTick, wasPlayerStalled As Boolean)
		If tick.position.IsNaNOrInfinity() OrElse tick.eyePos.IsNaNOrInfinity() Then
			Me.Kick("Kicked: Invalid Position")
			Return
		End If
		If tick.parentID <> Me.parentEntity.uid Then
			Return
		End If
		If Me.isMounted OrElse (Me.modelState IsNot Nothing AndAlso Me.modelState.mounted) OrElse (Me.modelStateTick IsNot Nothing AndAlso Me.modelStateTick.mounted) Then
			Return
		End If
		If Me.IsWounded() AndAlso Me.IsRestrained Then
			Return
		End If
		If wasPlayerStalled Then
			Dim num As Single = Vector3.Distance(tick.position, Me.tickInterpolator.EndPoint)
			If num > 0.01F Then
				Global.AntiHack.ResetTimer(Me)
			End If
			If num > 0.5F Then
				MyBase.ClientRPC(Of Vector3, NetworkableId)(RpcTarget.Player("ForcePositionToParentOffset", Me), Me.tickInterpolator.EndPoint, Me.parentEntity.uid)
			End If
			Return
		End If
		If(Me.modelState Is Nothing OrElse Not Me.modelState.flying OrElse (Not Me.IsAdmin AndAlso Not Me.IsDeveloper)) AndAlso Vector3.Distance(tick.position, Me.tickInterpolator.EndPoint) > 5F Then
			Global.AntiHack.ResetTimer(Me)
			MyBase.ClientRPC(Of Vector3, NetworkableId)(RpcTarget.Player("ForcePositionToParentOffset", Me), Me.tickInterpolator.EndPoint, Me.parentEntity.uid)
			Return
		End If
		Me.tickInterpolator.AddPoint(tick.position)
		Me.tickNeedsFinalizing = True
	End Sub

	' Token: 0x06000784 RID: 1924 RVA: 0x00058410 File Offset: 0x00056610
	Friend Sub UpdateRotationFromTick(tick As PlayerTick)
		If tick.inputState Is Nothing Then
			Return
		End If
		If tick.inputState.aimAngles.IsNaNOrInfinity() Then
			Me.Kick("Kicked: Invalid Rotation")
			Return
		End If
		Me.tickViewAngles = tick.inputState.aimAngles
		Me.tickNeedsFinalizing = True
	End Sub

	' Token: 0x06000785 RID: 1925 RVA: 0x0005845C File Offset: 0x0005665C
	Public Sub UpdateEstimatedVelocity(lastPos As Vector3, currentPos As Vector3, deltaTime As Single)
		Me.estimatedVelocity = (currentPos - lastPos) / deltaTime
		Me.estimatedSpeed = Me.estimatedVelocity.magnitude
		Me.estimatedSpeed2D = Me.estimatedVelocity.Magnitude2D()
		If Me.estimatedSpeed < 0.01F Then
			Me.estimatedSpeed = 0F
		End If
		If Me.estimatedSpeed2D < 0.01F Then
			Me.estimatedSpeed2D = 0F
		End If
	End Sub

	' Token: 0x170000E1 RID: 225
	' (get) Token: 0x06000786 RID: 1926 RVA: 0x000584D1 File Offset: 0x000566D1
	' (set) Token: 0x06000787 RID: 1927 RVA: 0x000584D9 File Offset: 0x000566D9
	Public Property tickViewAngles As Vector3

	' Token: 0x170000E2 RID: 226
	' (get) Token: 0x06000788 RID: 1928 RVA: 0x000584E2 File Offset: 0x000566E2
	Public ReadOnly Property tickHistoryCapacity As Integer
		Get
			Return Mathf.Max(1, Mathf.CeilToInt(Me.ticksPerSecond.Calculate() * ConVar.AntiHack.tickhistorytime))
		End Get
	End Property

	' Token: 0x170000E3 RID: 227
	' (get) Token: 0x06000789 RID: 1929 RVA: 0x00058502 File Offset: 0x00056702
	Public ReadOnly Property tickHistoryMatrix As Matrix4x4
		Get
			If Not MyBase.transform.parent Then
				Return Matrix4x4.identity
			End If
			Return MyBase.transform.parent.localToWorldMatrix
		End Get
	End Property

	' Token: 0x0600078A RID: 1930 RVA: 0x0005852C File Offset: 0x0005672C
	Private Sub FinalizeTick(deltaTime As Single)
		Me.tickDeltaTime += deltaTime
		If Me.IsReceivingSnapshot Then
			Return
		End If
		If Not Me.tickNeedsFinalizing Then
			Return
		End If
		Me.tickNeedsFinalizing = False
		Using TimeWarning.[New]("ModelState", 0)
			If Me.modelStateTick IsNot Nothing Then
				If Me.modelStateTick.flying AndAlso Not Me.IsAdmin AndAlso Not Me.IsDeveloper Then
					Global.AntiHack.NoteAdminHack(Me)
				End If
				If Me.modelStateTick.inheritedVelocity <> Vector3.zero AndAlso MyBase.FindTrigger(Of TriggerForce)() Is Nothing Then
					Me.modelStateTick.inheritedVelocity = Vector3.zero
				End If
				If Me.modelState IsNot Nothing Then
					If ConVar.AntiHack.modelstate AndAlso Me.TriggeredAntiHack(1F, Single.PositiveInfinity) Then
						Me.modelStateTick.ducked = Me.modelState.ducked
					End If
					Me.modelState.ResetToPool()
					Me.modelState = Nothing
				End If
				Me.modelState = Me.modelStateTick
				Me.modelStateTick = Nothing
				Me.UpdateModelState()
			End If
		End Using
		Using TimeWarning.[New]("Transform", 0)
			Me.UpdateEstimatedVelocity(Me.tickInterpolator.StartPoint, Me.tickInterpolator.EndPoint, Me.tickDeltaTime)
			Dim flag As Boolean = Me.tickInterpolator.StartPoint <> Me.tickInterpolator.EndPoint
			Dim flag2 As Boolean = Me.tickViewAngles <> Me.viewAngles
			If flag Then
				If Global.AntiHack.ValidateMove(Me, Me.tickInterpolator, Me.tickDeltaTime) Then
					MyBase.transform.localPosition = Me.tickInterpolator.EndPoint
					Me.ticksPerSecond.Increment()
					Me.tickHistory.AddPoint(Me.tickInterpolator.EndPoint, Me.tickHistoryCapacity)
					Global.AntiHack.FadeViolations(Me, Me.tickDeltaTime)
				Else
					flag = False
					If ConVar.AntiHack.forceposition Then
						MyBase.ClientRPC(Of Vector3, NetworkableId)(RpcTarget.Player("ForcePositionToParentOffset", Me), MyBase.transform.localPosition, Me.parentEntity.uid)
					End If
				End If
			End If
			Me.tickInterpolator.Reset(MyBase.transform.localPosition)
			If flag2 Then
				Me.viewAngles = Me.tickViewAngles
				If Not Me.isMounted OrElse Not Me.GetMounted().isMobile Then
					MyBase.transform.rotation = Quaternion.identity
				End If
				MyBase.transform.hasChanged = True
			End If
			If flag OrElse flag2 Then
				Me.eyes.NetworkUpdate(Quaternion.Euler(Me.viewAngles))
				MyBase.NetworkPositionTick()
			End If
			Global.AntiHack.ValidateEyeHistory(Me)
		End Using
		Using TimeWarning.[New]("ModelState", 0)
			If Me.modelState IsNot Nothing Then
				Me.modelState.waterLevel = Me.WaterFactor()
			End If
		End Using
		Using TimeWarning.[New]("EACStateUpdate", 0)
			Me.EACStateUpdate()
		End Using
		Using TimeWarning.[New]("AntiHack.EnforceViolations", 0)
			Global.AntiHack.EnforceViolations(Me)
		End Using
		Me.tickDeltaTime = 0F
	End Sub

	' Token: 0x170000E4 RID: 228
	' (get) Token: 0x0600078B RID: 1931 RVA: 0x000588AC File Offset: 0x00056AAC
	' (set) Token: 0x0600078C RID: 1932 RVA: 0x000588B4 File Offset: 0x00056AB4
	Public Property CurrentTutorialAllowance As Global.BasePlayer.TutorialItemAllowance

	' Token: 0x0600078D RID: 1933 RVA: 0x000588C0 File Offset: 0x00056AC0
	Public Function IsCraftingTutorialBlocked(def As ItemDefinition, <System.Runtime.InteropServices.OutAttribute()> ByRef forceUnlock As Boolean) As Boolean
		forceUnlock = False
		If Not Me.IsInTutorial Then
			Return False
		End If
		If def.tutorialAllowance = Global.BasePlayer.TutorialItemAllowance.None Then
			Return True
		End If
		Dim flag As Boolean = Me.CurrentTutorialAllowance >= def.tutorialAllowance
		If flag AndAlso def.Blueprint IsNot Nothing AndAlso Not def.Blueprint.defaultBlueprint Then
			forceUnlock = True
		End If
		Return Not flag
	End Function

	' Token: 0x0600078E RID: 1934 RVA: 0x00058919 File Offset: 0x00056B19
	Public Function CanModifyCraftAmountDuringTutorial() As Boolean
		Return Me.IsInTutorial AndAlso Me.CurrentTutorialAllowance >= Global.BasePlayer.TutorialItemAllowance.Level4_Spear_Fire
	End Function

	' Token: 0x0600078F RID: 1935 RVA: 0x00058934 File Offset: 0x00056B34
	Public Function GetCurrentTutorialIsland() As Global.TutorialIsland
		If Not Me.IsInTutorial Then
			Return Nothing
		End If
		For Each tutorialIsland As Global.TutorialIsland In Global.TutorialIsland.GetTutorialList(MyBase.isServer)
			If tutorialIsland.ForPlayer.[Get](MyBase.isServer) Is Me Then
				Return tutorialIsland
			End If
		Next
		Return Nothing
	End Function

	' Token: 0x06000790 RID: 1936 RVA: 0x000589B0 File Offset: 0x00056BB0
	Public Sub ClearTutorial()
		Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.IsInTutorial, False)
		Global.SleepingBag.ClearTutorialBagsForPlayer(Me.userID)
	End Sub

	' Token: 0x06000791 RID: 1937 RVA: 0x000589CE File Offset: 0x00056BCE
	Public Sub ClearTutorial_PostDeath()
		Me.ClearAllPings()
		Me.ClearDeathMarker(False)
		Me.WipeMissions()
		Me.SendPingsToClient()
		Me.SendMarkersToClient()
	End Sub

	' Token: 0x06000792 RID: 1938 RVA: 0x000589EF File Offset: 0x00056BEF
	Public Sub OnStartedTutorial()
		Me.ClearAllPings()
		Me.WipeMissions()
	End Sub

	' Token: 0x06000793 RID: 1939 RVA: 0x000589FD File Offset: 0x00056BFD
	Public Sub SetTutorialAllowance(newAllowance As Global.BasePlayer.TutorialItemAllowance)
		If newAllowance < Me.CurrentTutorialAllowance Then
			Return
		End If
		Me.CurrentTutorialAllowance = newAllowance
		MyBase.SendNetworkUpdate(Global.BasePlayer.NetworkQueue.Update)
	End Sub

	' Token: 0x06000794 RID: 1940 RVA: 0x00058A17 File Offset: 0x00056C17
	<Global.BaseEntity.RPC_Server()>
	Private Sub StartTutorial(msg As Global.BaseEntity.RPCMessage)
		If msg.player IsNot Me Then
			Return
		End If
		Me.StartTutorial(True)
	End Sub

	' Token: 0x06000795 RID: 1941 RVA: 0x00058A30 File Offset: 0x00056C30
	Public Sub StartTutorial(triggerAnalytics As Boolean)
		If Not ConVar.Server.tutorialEnabled Then
			Return
		End If
		If Not Global.TutorialIsland.HasAvailableTutorialIsland Then
			Me.ShowToast(GameTip.Styles.Red_Normal, Global.TutorialIsland.NoTutorialIslandsAvailablePhrase, Array.Empty(Of String)())
			Return
		End If
		If Me.startTutorialCooldown > UnityEngine.Time.realtimeSinceStartup Then
			Dim num As Integer = Mathf.CeilToInt(Me.startTutorialCooldown - UnityEngine.Time.realtimeSinceStartup)
			Me.ShowToast(GameTip.Styles.Red_Normal, Global.TutorialIsland.TutorialIslandStartCooldown, New String() { num.ToString() })
			Return
		End If
		Me.startTutorialCooldown = UnityEngine.Time.realtimeSinceStartup + CSng(Debugging.tutorial_start_cooldown)
		MyBase.Hurt(99999F)
		Me.Respawn()
		Global.TutorialIsland.RestoreOrCreateIslandForPlayer(Me, triggerAnalytics)
	End Sub

	' Token: 0x06000796 RID: 1942 RVA: 0x00058AC5 File Offset: 0x00056CC5
	<Global.BaseEntity.RPC_Server()>
	<Global.BaseEntity.RPC_Server.CallsPerSecond(1UL)>
	Private Sub PlayerRequestedTutorialStart(msg As Global.BaseEntity.RPCMessage)
		If Not ConVar.Server.tutorialEnabled Then
			Return
		End If
		If Not Global.TutorialIsland.HasAvailableTutorialIsland Then
			Me.ShowToast(GameTip.Styles.Red_Normal, Global.TutorialIsland.NoTutorialIslandsAvailablePhrase, Array.Empty(Of String)())
			Return
		End If
		MyBase.ClientRPC(RpcTarget.Player("PromptToStartTutorial", Me))
	End Sub

	' Token: 0x06000797 RID: 1943 RVA: 0x00058AFC File Offset: 0x00056CFC
	Public Function GetUnderwearSkin() As UInteger
		Dim infoInt As UInteger = CUInt(Me.GetInfoInt("client.underwearskin", 0))
		If infoInt <> Me.lastValidUnderwearSkin AndAlso UnityEngine.Time.time > Me.nextUnderwearValidationTime Then
			Dim underwearManifest As UnderwearManifest = UnderwearManifest.[Get]()
			Me.nextUnderwearValidationTime = UnityEngine.Time.time + 0.2F
			Dim underwear As Underwear = underwearManifest.GetUnderwear(infoInt)
			If underwear Is Nothing Then
				Me.lastValidUnderwearSkin = 0UI
			ElseIf Underwear.Validate(underwear, Me) Then
				Me.lastValidUnderwearSkin = infoInt
			End If
		End If
		Return Me.lastValidUnderwearSkin
	End Function

	' Token: 0x06000798 RID: 1944 RVA: 0x00058B74 File Offset: 0x00056D74
	<Global.BaseEntity.RPC_Server()>
	Public Sub ServerRPC_UnderwearChange(msg As Global.BaseEntity.RPCMessage)
		If msg.player IsNot Me Then
			Return
		End If
		Dim num As UInteger = Me.lastValidUnderwearSkin
		Dim underwearSkin As UInteger = Me.GetUnderwearSkin()
		If num <> underwearSkin Then
			MyBase.SendNetworkUpdate(Global.BasePlayer.NetworkQueue.Update)
		End If
	End Sub

	' Token: 0x06000799 RID: 1945 RVA: 0x00058BA7 File Offset: 0x00056DA7
	Public Function IsWounded() As Boolean
		Return Me.HasPlayerFlag(Global.BasePlayer.PlayerFlags.Wounded)
	End Function

	' Token: 0x0600079A RID: 1946 RVA: 0x00058BB1 File Offset: 0x00056DB1
	Public Function IsCrawling() As Boolean
		Return Me.HasPlayerFlag(Global.BasePlayer.PlayerFlags.Wounded) AndAlso Not Me.HasPlayerFlag(Global.BasePlayer.PlayerFlags.Incapacitated)
	End Function

	' Token: 0x0600079B RID: 1947 RVA: 0x00058BCD File Offset: 0x00056DCD
	Public Function IsIncapacitated() As Boolean
		Return Me.HasPlayerFlag(Global.BasePlayer.PlayerFlags.Incapacitated)
	End Function

	' Token: 0x170000E5 RID: 229
	' (get) Token: 0x0600079C RID: 1948 RVA: 0x00058BDA File Offset: 0x00056DDA
	Public ReadOnly Property TimeSinceWoundedStarted As Single
		Get
			Return UnityEngine.Time.realtimeSinceStartup - Me.lastWoundedStartTime
		End Get
	End Property

	' Token: 0x0600079D RID: 1949 RVA: 0x00058BE8 File Offset: 0x00056DE8
	Private Function WoundInsteadOfDying(info As HitInfo) As Boolean
		If Not Me.EligibleForWounding(info) Then
			Return False
		End If
		Me.BecomeWounded(info)
		Return True
	End Function

	' Token: 0x0600079E RID: 1950 RVA: 0x00058BFD File Offset: 0x00056DFD
	Private Sub ResetWoundingVars()
		MyBase.CancelInvoke(AddressOf Me.WoundingTick)
		Me.woundedDuration = 0F
		Me.lastWoundedStartTime = Single.NegativeInfinity
		Me.healingWhileCrawling = 0F
		Me.woundedByFallDamage = False
	End Sub

	' Token: 0x0600079F RID: 1951 RVA: 0x00058C3C File Offset: 0x00056E3C
	Public Overridable Function EligibleForWounding(info As HitInfo) As Boolean
		If Not ConVar.Server.woundingenabled Then
			Return False
		End If
		If Me.IsWounded() Then
			Return False
		End If
		If Me.IsSleeping() Then
			Return False
		End If
		If Me.isMounted Then
			Return False
		End If
		If info Is Nothing Then
			Return False
		End If
		If Not Me.IsWounded() AndAlso UnityEngine.Time.realtimeSinceStartup - Me.lastWoundedStartTime < ConVar.Server.rewounddelay Then
			Return False
		End If
		Dim activeGameMode As BaseGameMode = BaseGameMode.GetActiveGameMode(True)
		If activeGameMode AndAlso Not activeGameMode.allowWounding Then
			Return False
		End If
		If Me.triggers IsNot Nothing Then
			For i As Integer = 0 To Me.triggers.Count - 1
				If TypeOf Me.triggers(i)Is IHurtTrigger Then
					Return False
				End If
			Next
		End If
		If TypeOf info.WeaponPrefab Is BaseMelee Then
			Return True
		End If
		If TypeOf info.WeaponPrefab Is Global.BaseProjectile Then
			Return Not info.isHeadshot
		End If
		Dim majorityDamageType As DamageType = info.damageTypes.GetMajorityDamageType()
		Return majorityDamageType <> DamageType.Suicide AndAlso (majorityDamageType = DamageType.Fall OrElse majorityDamageType = DamageType.Bite OrElse majorityDamageType = DamageType.Bleeding OrElse majorityDamageType = DamageType.Hunger OrElse majorityDamageType = DamageType.Thirst OrElse majorityDamageType = DamageType.Poison)
	End Function

	' Token: 0x060007A0 RID: 1952 RVA: 0x00058D40 File Offset: 0x00056F40
	Public Sub BecomeWounded(Optional info As HitInfo = Nothing)
		If Me.IsWounded() Then
			Return
		End If
		Dim flag As Boolean = info IsNot Nothing AndAlso info.damageTypes.GetMajorityDamageType() = DamageType.Fall
		If Me.IsCrawling() Then
			Me.woundedByFallDamage = (Me.woundedByFallDamage OrElse flag)
			Me.GoToIncapacitated(info)
			Return
		End If
		Me.woundedByFallDamage = flag
		If flag OrElse Not ConVar.Server.crawlingenabled Then
			Me.GoToIncapacitated(info)
			Return
		End If
		Me.GoToCrawling(info)
	End Sub

	' Token: 0x060007A1 RID: 1953 RVA: 0x00058DAA File Offset: 0x00056FAA
	Public Sub StopWounded(Optional source As Global.BasePlayer = Nothing)
		If Not Me.IsWounded() Then
			Return
		End If
		Me.RecoverFromWounded()
		MyBase.CancelInvoke(AddressOf Me.WoundingTick)
		EACServer.LogPlayerRevive(source, Me)
	End Sub

	' Token: 0x060007A2 RID: 1954 RVA: 0x00058DD4 File Offset: 0x00056FD4
	Public Sub ProlongWounding(delay As Single)
		If Me.IsRestrained Then
			Return
		End If
		Me.woundedDuration = Mathf.Max(Me.woundedDuration, Mathf.Min(Me.TimeSinceWoundedStarted + delay, Me.woundedDuration + delay))
		Me.SendWoundedInformation(Me.woundedDuration)
	End Sub

	' Token: 0x060007A3 RID: 1955 RVA: 0x00058E14 File Offset: 0x00057014
	Public Sub SendWoundedInformation(timeLeft As Single)
		Dim recoveryChance As Single = Me.GetRecoveryChance()
		MyBase.ClientRPC(Of Single, Single, Single)(RpcTarget.Player("CLIENT_GetWoundedInformation", Me), recoveryChance, timeLeft, Me.woundedDuration)
	End Sub

	' Token: 0x060007A4 RID: 1956 RVA: 0x00058E44 File Offset: 0x00057044
	Public Function GetRecoveryChance() As Single
		Dim num As Single = If(Me.IsIncapacitated(), ConVar.Server.incapacitatedrecoverchance, ConVar.Server.woundedrecoverchance)
		Dim t As Single = (Me.metabolism.hydration.Fraction() + Me.metabolism.calories.Fraction()) / 2F
		Dim num2 As Single = Mathf.Lerp(0F, ConVar.Server.woundedmaxfoodandwaterbonus, t)
		Dim result As Single = Mathf.Clamp01(num + num2)
		Dim itemDefinition As ItemDefinition = ItemManager.FindItemDefinition("largemedkit")
		If Me.inventory.containerBelt.FindItemByItemID(itemDefinition.itemid) IsNot Nothing AndAlso Not Me.woundedByFallDamage Then
			Return 1F
		End If
		Return result
	End Function

	' Token: 0x060007A5 RID: 1957 RVA: 0x00058ED8 File Offset: 0x000570D8
	Private Sub WoundingTick()
		Using TimeWarning.[New]("WoundingTick", 0)
			If Not Me.IsDead() Then
				If Not Player.woundforever AndAlso Me.TimeSinceWoundedStarted >= Me.woundedDuration Then
					Dim num As Single = If(Me.IsIncapacitated(), ConVar.Server.incapacitatedrecoverchance, ConVar.Server.woundedrecoverchance)
					Dim t As Single = (Me.metabolism.hydration.Fraction() + Me.metabolism.calories.Fraction()) / 2F
					Dim num2 As Single = Mathf.Lerp(0F, ConVar.Server.woundedmaxfoodandwaterbonus, t)
					Dim num3 As Single = Mathf.Clamp01(num + num2)
					If UnityEngine.Random.value < num3 Then
						Me.RecoverFromWounded()
					ElseIf Me.woundedByFallDamage Then
						Me.Die(Nothing)
					Else
						Dim itemDefinition As ItemDefinition = ItemManager.FindItemDefinition("largemedkit")
						Dim item As Global.Item = Me.inventory.containerBelt.FindItemByItemID(itemDefinition.itemid)
						If item IsNot Nothing Then
							item.UseItem(1)
							Me.RecoverFromWounded()
						Else
							Me.Die(Nothing)
						End If
					End If
				Else
					If Me.IsSwimming() AndAlso Me.IsCrawling() Then
						Me.GoToIncapacitated(Nothing)
					End If
					MyBase.Invoke(AddressOf Me.WoundingTick, 1F)
				End If
			End If
		End Using
	End Sub

	' Token: 0x060007A6 RID: 1958 RVA: 0x0005902C File Offset: 0x0005722C
	Private Sub GoToCrawling(info As HitInfo)
		MyBase.health = CSng(UnityEngine.Random.Range(ConVar.Server.crawlingminimumhealth, ConVar.Server.crawlingmaximumhealth))
		Me.metabolism.bleeding.value = 0F
		Me.healingWhileCrawling = 0F
		Me.WoundedStartSharedCode(info)
		Me.StartWoundedTick(40, 50)
		Me.SendWoundedInformation(Me.woundedDuration)
		MyBase.SendNetworkUpdateImmediate(False)
	End Sub

	' Token: 0x060007A7 RID: 1959 RVA: 0x00059094 File Offset: 0x00057294
	Public Sub GoToIncapacitated(info As HitInfo)
		If Not Me.IsWounded() Then
			Me.WoundedStartSharedCode(info)
		End If
		MyBase.health = UnityEngine.Random.Range(2F, 6F)
		Me.metabolism.bleeding.value = 0F
		Me.healingWhileCrawling = 0F
		Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.Incapacitated, True)
		Me.SetServerFall(True)
		Me.inventory.DropBackpackOnDeath()
		Me.StartWoundedTick(10, 25)
		Me.SendWoundedInformation(Me.woundedDuration)
		MyBase.SendNetworkUpdateImmediate(False)
	End Sub

	' Token: 0x060007A8 RID: 1960 RVA: 0x00059120 File Offset: 0x00057320
	Private Sub WoundedStartSharedCode(info As HitInfo)
		Me.stats.Add("wounded", 1, CType(5, Global.Stats))
		Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.Wounded, True)
		If BaseGameMode.GetActiveGameMode(MyBase.isServer) Then
			BaseGameMode.GetActiveGameMode(MyBase.isServer).OnPlayerWounded(info.InitiatorPlayer, Me, info)
		End If
	End Sub

	' Token: 0x060007A9 RID: 1961 RVA: 0x00059172 File Offset: 0x00057372
	Private Sub StartWoundedTick(minTime As Integer, maxTime As Integer)
		Me.woundedDuration = CSng(UnityEngine.Random.Range(minTime, maxTime + 1))
		Me.ApplyWoundedStartTime()
		MyBase.Invoke(AddressOf Me.WoundingTick, 1F)
	End Sub

	' Token: 0x060007AA RID: 1962 RVA: 0x000591A1 File Offset: 0x000573A1
	Public Sub ApplyWoundedStartTime()
		Me.lastWoundedStartTime = UnityEngine.Time.realtimeSinceStartup
	End Sub

	' Token: 0x060007AB RID: 1963 RVA: 0x000591B0 File Offset: 0x000573B0
	Private Sub RecoverFromWounded()
		If Me.IsCrawling() Then
			MyBase.health = UnityEngine.Random.Range(2F, 6F) + Me.healingWhileCrawling
		End If
		Me.healingWhileCrawling = 0F
		Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.Wounded, False)
		Me.SetPlayerFlag(Global.BasePlayer.PlayerFlags.Incapacitated, False)
		If BaseGameMode.GetActiveGameMode(MyBase.isServer) Then
			BaseGameMode.GetActiveGameMode(MyBase.isServer).OnPlayerRevived(Nothing, Me)
		End If
	End Sub

	' Token: 0x060007AC RID: 1964 RVA: 0x00059225 File Offset: 0x00057425
	Private Function WoundingCausingImmortality(info As HitInfo) As Boolean
		Return Me.IsWounded() AndAlso Me.TimeSinceWoundedStarted <= 0.25F AndAlso (info Is Nothing OrElse info.damageTypes.GetMajorityDamageType() <> DamageType.Fall)
	End Function

	' Token: 0x060007AD RID: 1965 RVA: 0x00059255 File Offset: 0x00057455
	Public Overrides Function ToPlayer() As Global.BasePlayer
		Return Me
	End Function

	' Token: 0x170000E6 RID: 230
	' (get) Token: 0x060007AE RID: 1966 RVA: 0x00059258 File Offset: 0x00057458
	Public ReadOnly Property Connection As Network.Connection
		Get
			If Me.net IsNot Nothing Then
				Return Me.net.connection
			End If
			Return Nothing
		End Get
	End Property

	' Token: 0x170000E7 RID: 231
	' (get) Token: 0x060007AF RID: 1967 RVA: 0x0005926F File Offset: 0x0005746F
	Public ReadOnly Property IsBot As Boolean
		Get
			Return Me.userID < 10000000UL
		End Get
	End Property

	' Token: 0x170000E8 RID: 232
	' (get) Token: 0x060007B0 RID: 1968 RVA: 0x00059284 File Offset: 0x00057484
	' (set) Token: 0x060007B1 RID: 1969 RVA: 0x00059297 File Offset: 0x00057497
	Public Property eyes As PlayerEyes
		Get
			Dim hiddenValue As Global.BasePlayer.HiddenValue(Of PlayerEyes) = Me.eyesValue
			If hiddenValue Is Nothing Then
				Return Nothing
			End If
			Return hiddenValue.[Get]()
		End Get
		Set(value As PlayerEyes)
			Me.eyesValue.[Set](value)
		End Set
	End Property

	' Token: 0x170000E9 RID: 233
	' (get) Token: 0x060007B2 RID: 1970 RVA: 0x000592A6 File Offset: 0x000574A6
	Public ReadOnly Property inventory As Global.PlayerInventory
		Get
			Dim hiddenValue As Global.BasePlayer.HiddenValue(Of Global.PlayerInventory) = Me.inventoryValue
			If hiddenValue Is Nothing Then
				Return Nothing
			End If
			Return hiddenValue.[Get]()
		End Get
	End Property

	' Token: 0x170000EA RID: 234
	' (get) Token: 0x060007B3 RID: 1971 RVA: 0x000592B9 File Offset: 0x000574B9
	Private ReadOnly Property playerCollider As CapsuleCollider
		Get
			Dim hiddenValue As Global.BasePlayer.HiddenValue(Of CapsuleCollider) = Me.colliderValue
			If hiddenValue Is Nothing Then
				Return Nothing
			End If
			Return hiddenValue.[Get]()
		End Get
	End Property

	' Token: 0x170000EB RID: 235
	' (get) Token: 0x060007B4 RID: 1972 RVA: 0x000592CC File Offset: 0x000574CC
	' (set) Token: 0x060007B5 RID: 1973 RVA: 0x000592EB File Offset: 0x000574EB
	Public Property displayName As String
		Get
			Return NameHelper.[Get](Me.userID, Me._displayName, MyBase.isClient, False)
		End Get
		Set(value As String)
			If Me._lastSetName = value Then
				Return
			End If
			Me._lastSetName = value
			Me._displayName = Global.BasePlayer.SanitizePlayerNameString(value, Me.userID)
		End Set
	End Property

	' Token: 0x060007B6 RID: 1974 RVA: 0x0005931A File Offset: 0x0005751A
	Public Shared Function SanitizePlayerNameString(playerName As String, userId As ULong) As String
		playerName = playerName.ToPrintable(32).EscapeRichText().Trim()
		If String.IsNullOrWhiteSpace(playerName) Then
			playerName = userId.ToString()
		End If
		Return playerName
	End Function

	' Token: 0x060007B7 RID: 1975 RVA: 0x00059344 File Offset: 0x00057544
	Public Function IsGod() As Boolean
		Return MyBase.isServer AndAlso (Me.IsAdmin OrElse Me.IsDeveloper) AndAlso Me.IsConnected AndAlso Me.net.connection IsNot Nothing AndAlso Me.net.connection.info.GetBool("global.god", False)
	End Function

	' Token: 0x060007B8 RID: 1976 RVA: 0x0005939E File Offset: 0x0005759E
	Public Overrides Function GetNetworkRotation() As Quaternion
		If MyBase.isServer Then
			Return Quaternion.Euler(Me.viewAngles)
		End If
		Return Quaternion.identity
	End Function

	' Token: 0x060007B9 RID: 1977 RVA: 0x000593B9 File Offset: 0x000575B9
	Public Function CanInteract() As Boolean
		Return Me.CanInteract(False)
	End Function

	' Token: 0x060007BA RID: 1978 RVA: 0x000593C4 File Offset: 0x000575C4
	Public Function CanInteract(usableWhileCrawling As Boolean) As Boolean
		Dim flag As Boolean = Me.CurrentGestureIsSurrendering
		If Not flag AndAlso Me.IsRestrained Then
			Dim restraintItem As Handcuffs = Me.Belt.GetRestraintItem()
			flag = (restraintItem IsNot Nothing AndAlso restraintItem.BlockUse)
		End If
		Return Not Me.IsDead() AndAlso Not Me.IsSleeping() AndAlso Not Me.IsSpectating() AndAlso If(usableWhileCrawling, (Not Me.IsIncapacitated()), (Not Me.IsWounded())) AndAlso Not Me.HasActiveTelephone AndAlso Not flag
	End Function

	' Token: 0x060007BB RID: 1979 RVA: 0x00059441 File Offset: 0x00057641
	Public Overrides Function StartHealth() As Single
		Return UnityEngine.Random.Range(50F, 60F)
	End Function

	' Token: 0x060007BC RID: 1980 RVA: 0x00059452 File Offset: 0x00057652
	Public Overrides Function StartMaxHealth() As Single
		Return 100F
	End Function

	' Token: 0x060007BD RID: 1981 RVA: 0x00059459 File Offset: 0x00057659
	Public Overrides Function MaxHealth() As Single
		Return 100F * (1F + If((Me.modifiers IsNot Nothing), Me.modifiers.GetValue(Global.Modifier.ModifierType.Max_Health, 0F), 0F))
	End Function

	' Token: 0x060007BE RID: 1982 RVA: 0x0005948D File Offset: 0x0005768D
	Public Overrides Function MaxVelocity() As Single
		If Me.IsSleeping() Then
			Return 0F
		End If
		If Me.isMounted Then
			Return Me.GetMounted().MaxVelocity()
		End If
		Return Me.GetMaxSpeed()
	End Function

	' Token: 0x060007BF RID: 1983 RVA: 0x000594B8 File Offset: 0x000576B8
	Public Overrides Function WorldSpaceBounds() As OBB
		If Me.IsSleeping() Then
			Dim center As Vector3 = Me.bounds.center
			Dim size As Vector3 = Me.bounds.size
			center.y /= 2F
			size.y /= 2F
			Return New OBB(MyBase.transform.position, MyBase.transform.lossyScale, MyBase.transform.rotation, New Bounds(center, size))
		End If
		Return MyBase.WorldSpaceBounds()
	End Function

	' Token: 0x060007C0 RID: 1984 RVA: 0x0005953C File Offset: 0x0005773C
	Public Function GetMountVelocity() As Vector3
		Dim baseMountable As BaseMountable = Me.GetMounted()
		If Not(baseMountable IsNot Nothing) Then
			Return Vector3.zero
		End If
		Return baseMountable.GetWorldVelocity()
	End Function

	' Token: 0x060007C1 RID: 1985 RVA: 0x00059568 File Offset: 0x00057768
	Public Overrides Function GetInheritedProjectileVelocity(direction As Vector3) As Vector3
		Dim baseMountable As BaseMountable = Me.GetMounted()
		If Not baseMountable Then
			Return MyBase.GetInheritedProjectileVelocity(direction)
		End If
		Return baseMountable.GetInheritedProjectileVelocity(direction)
	End Function

	' Token: 0x060007C2 RID: 1986 RVA: 0x00059594 File Offset: 0x00057794
	Public Overrides Function GetInheritedThrowVelocity(direction As Vector3) As Vector3
		Dim baseMountable As BaseMountable = Me.GetMounted()
		If Not baseMountable Then
			Return MyBase.GetInheritedThrowVelocity(direction)
		End If
		Return baseMountable.GetInheritedThrowVelocity(direction)
	End Function

	' Token: 0x060007C3 RID: 1987 RVA: 0x000595C0 File Offset: 0x000577C0
	Public Overrides Function GetInheritedDropVelocity() As Vector3
		Dim baseMountable As BaseMountable = Me.GetMounted()
		If Not baseMountable Then
			Return MyBase.GetInheritedDropVelocity()
		End If
		Return baseMountable.GetInheritedDropVelocity()
	End Function

	' Token: 0x060007C4 RID: 1988 RVA: 0x000595EC File Offset: 0x000577EC
	Public Overrides Sub PreInitShared()
		MyBase.PreInitShared()
		Me.cachedProtection = ScriptableObject.CreateInstance(Of ProtectionProperties)()
		Me.baseProtection = ScriptableObject.CreateInstance(Of ProtectionProperties)()
		Me.inventoryValue.[Set](MyBase.GetComponent(Of Global.PlayerInventory)())
		Me.blueprints = MyBase.GetComponent(Of PlayerBlueprints)()
		Me.metabolism = MyBase.GetComponent(Of Global.PlayerMetabolism)()
		Me.modifiers = MyBase.GetComponent(Of Global.PlayerModifiers)()
		Me.colliderValue.[Set](MyBase.GetComponent(Of CapsuleCollider)())
		Me.eyesValue.[Set](MyBase.GetComponent(Of PlayerEyes)())
		Me.playerColliderStanding = New Global.BasePlayer.CapsuleColliderInfo(Me.playerCollider.height, Me.playerCollider.radius, Me.playerCollider.center)
		Me.playerColliderDucked = New Global.BasePlayer.CapsuleColliderInfo(1.5F, Me.playerCollider.radius, Vector3.up * 0.75F)
		Me.playerColliderCrawling = New Global.BasePlayer.CapsuleColliderInfo(Me.playerCollider.radius, Me.playerCollider.radius, Vector3.up * Me.playerCollider.radius)
		Me.playerColliderLyingDown = New Global.BasePlayer.CapsuleColliderInfo(0.4F, Me.playerCollider.radius, Vector3.up * 0.2F)
		Me.Belt = New PlayerBelt(Me)
	End Sub

	' Token: 0x060007C5 RID: 1989 RVA: 0x00059731 File Offset: 0x00057931
	Public Overrides Sub DestroyShared()
		UnityEngine.[Object].Destroy(Me.cachedProtection)
		UnityEngine.[Object].Destroy(Me.baseProtection)
		MyBase.DestroyShared()
	End Sub

	' Token: 0x060007C6 RID: 1990 RVA: 0x0005974F File Offset: 0x0005794F
	Public Overrides Function InSafeZone() As Boolean
		Return MyBase.isServer AndAlso MyBase.InSafeZone()
	End Function

	' Token: 0x060007C7 RID: 1991 RVA: 0x00059761 File Offset: 0x00057961
	Public Function IsInNoRespawnZone() As Boolean
		Return MyBase.isServer AndAlso Me.InNoRespawnZone()
	End Function

	' Token: 0x060007C8 RID: 1992 RVA: 0x00059773 File Offset: 0x00057973
	Public Function IsOnATugboat() As Boolean
		Return TypeOf Me.GetMountedVehicle()Is Tugboat OrElse TypeOf MyBase.GetParentEntity()Is Tugboat
	End Function

	' Token: 0x060007C9 RID: 1993 RVA: 0x00059794 File Offset: 0x00057994
	Public Shared Sub ServerCycle(deltaTime As Single)
		For i As Integer = 0 To Global.BasePlayer.activePlayerList.Values.Count - 1
			If Global.BasePlayer.activePlayerList.Values(i) Is Nothing Then
				Dim listHashSet As ListHashSet(Of Global.BasePlayer) = Global.BasePlayer.activePlayerList
				Dim num As Integer = i
				i = num - 1
				listHashSet.RemoveAt(num)
			End If
		Next
		Dim list As List(Of Global.BasePlayer) = Facepunch.Pool.GetList(Of Global.BasePlayer)()
		For j As Integer = 0 To Global.BasePlayer.activePlayerList.Count - 1
			list.Add(Global.BasePlayer.activePlayerList(j))
		Next
		For k As Integer = 0 To list.Count - 1
			If Not(list(k) Is Nothing) Then
				list(k).ServerUpdate(deltaTime)
			End If
		Next
		For l As Integer = 0 To Global.BasePlayer.bots.Count - 1
			If Not(Global.BasePlayer.bots(l) Is Nothing) Then
				Global.BasePlayer.bots(l).ServerUpdateBots(deltaTime)
			End If
		Next
		If ConVar.Server.idlekick > 0 AndAlso ((SingletonComponent(Of ServerMgr).Instance.AvailableSlots <= 0 AndAlso ConVar.Server.idlekickmode = 1) OrElse ConVar.Server.idlekickmode = 2) Then
			For m As Integer = 0 To list.Count - 1
				If list(m).IdleTime >= CSng((ConVar.Server.idlekick * 60)) AndAlso (Not list(m).IsAdmin OrElse ConVar.Server.idlekickadmins <> 0) AndAlso (Not list(m).IsDeveloper OrElse ConVar.Server.idlekickadmins <> 0) Then
					list(m).Kick("Idle for " + ConVar.Server.idlekick.ToString() + " minutes")
				End If
			Next
		End If
		Facepunch.Pool.FreeList(Of Global.BasePlayer)(list)
	End Sub

	' Token: 0x060007CA RID: 1994 RVA: 0x00059928 File Offset: 0x00057B28
	Private Function ManuallyCheckSafezone() As Boolean
		If Not MyBase.isServer Then
			Return False
		End If
		Dim list As List(Of Collider) = Facepunch.Pool.GetList(Of Collider)()
		Global.Vis.Colliders(Of Collider)(MyBase.transform.position, 0F, list, -1, QueryTriggerInteraction.Collide)
		Using enumerator As List(Of Collider).Enumerator = list.GetEnumerator()
			While enumerator.MoveNext()
				If enumerator.Current.GetComponent(Of TriggerSafeZone)() IsNot Nothing Then
					Facepunch.Pool.FreeList(Of Collider)(list)
					Return True
				End If
			End While
		End Using
		Facepunch.Pool.FreeList(Of Collider)(list)
		Return False
	End Function

	' Token: 0x060007CB RID: 1995 RVA: 0x000599B8 File Offset: 0x00057BB8
	Public Overrides Function OnStartBeingLooted(baseEntity As Global.BasePlayer) As Boolean
		If(baseEntity.InSafeZone() OrElse Me.InSafeZone() OrElse Me.ManuallyCheckSafezone()) AndAlso baseEntity.userID <> Me.userID Then
			Return False
		End If
		If Global.RelationshipManager.ServerInstance IsNot Nothing Then
			If(Me.IsSleeping() OrElse Me.IsIncapacitated()) AndAlso Not Global.RelationshipManager.ServerInstance.HasRelations(baseEntity.userID, Me.userID) Then
				Global.RelationshipManager.ServerInstance.SetRelationship(baseEntity, Me, Global.RelationshipManager.RelationshipType.Acquaintance, 1, False)
			End If
			Global.RelationshipManager.ServerInstance.SetSeen(baseEntity, Me)
		End If
		If Me.IsCrawling() Then
			Me.GoToIncapacitated(Nothing)
		End If
		If Me.inventory.crafting IsNot Nothing Then
			Me.inventory.crafting.CancelAll(True)
		End If
		Return MyBase.OnStartBeingLooted(baseEntity)
	End Function

	' Token: 0x060007CC RID: 1996 RVA: 0x00059A8E File Offset: 0x00057C8E
	Public Function GetBounds(ducked As Boolean) As Bounds
		Return New Bounds(MyBase.transform.position + Me.GetOffset(ducked), Me.GetSize(ducked))
	End Function

	' Token: 0x060007CD RID: 1997 RVA: 0x00059AB3 File Offset: 0x00057CB3
	Public Function GetBounds() As Bounds
		Return Me.GetBounds(Me.modelState.ducked)
	End Function

	' Token: 0x060007CE RID: 1998 RVA: 0x00059AC6 File Offset: 0x00057CC6
	Public Function GetCenter(ducked As Boolean) As Vector3
		Return MyBase.transform.position + Me.GetOffset(ducked)
	End Function

	' Token: 0x060007CF RID: 1999 RVA: 0x00059ADF File Offset: 0x00057CDF
	Public Function GetCenter() As Vector3
		Return Me.GetCenter(Me.modelState.ducked)
	End Function

	' Token: 0x060007D0 RID: 2000 RVA: 0x00059AF2 File Offset: 0x00057CF2
	Public Function GetOffset(ducked As Boolean) As Vector3
		If ducked Then
			Return New Vector3(0F, 0.55F, 0F)
		End If
		Return New Vector3(0F, 0.9F, 0F)
	End Function

	' Token: 0x060007D1 RID: 2001 RVA: 0x00059B20 File Offset: 0x00057D20
	Public Function GetOffset() As Vector3
		Return Me.GetOffset(Me.modelState.ducked)
	End Function

	' Token: 0x060007D2 RID: 2002 RVA: 0x00059B33 File Offset: 0x00057D33
	Public Function GetSize(ducked As Boolean) As Vector3
		If ducked Then
			Return New Vector3(1F, 1.1F, 1F)
		End If
		Return New Vector3(1F, 1.8F, 1F)
	End Function

	' Token: 0x060007D3 RID: 2003 RVA: 0x00059B61 File Offset: 0x00057D61
	Public Function GetSize() As Vector3
		Return Me.GetSize(Me.modelState.ducked)
	End Function

	' Token: 0x060007D4 RID: 2004 RVA: 0x00059B74 File Offset: 0x00057D74
	Public Function GetHeight(ducked As Boolean) As Single
		If ducked Then
			Return 1.1F
		End If
		Return 1.8F
	End Function

	' Token: 0x060007D5 RID: 2005 RVA: 0x00059B84 File Offset: 0x00057D84
	Public Function GetHeight() As Single
		Return Me.GetHeight(Me.modelState.ducked)
	End Function

	' Token: 0x060007D6 RID: 2006 RVA: 0x00059B97 File Offset: 0x00057D97
	Public Function GetRadius() As Single
		Return 0.5F
	End Function

	' Token: 0x060007D7 RID: 2007 RVA: 0x00059B9E File Offset: 0x00057D9E
	Public Function GetJumpHeight() As Single
		Return 1.5F
	End Function

	' Token: 0x060007D8 RID: 2008 RVA: 0x00059BA5 File Offset: 0x00057DA5
	Public Overrides Function TriggerPoint() As Vector3
		Return MyBase.transform.position + Me.NoClipOffset()
	End Function

	' Token: 0x060007D9 RID: 2009 RVA: 0x00059BBD File Offset: 0x00057DBD
	Public Function NoClipOffset() As Vector3
		Return New Vector3(0F, Me.GetHeight(True) - Me.GetRadius(), 0F)
	End Function

	' Token: 0x060007DA RID: 2010 RVA: 0x00059BDC File Offset: 0x00057DDC
	Public Function NoClipRadius(margin As Single) As Single
		Return Me.GetRadius() - margin
	End Function

	' Token: 0x060007DB RID: 2011 RVA: 0x00059BE6 File Offset: 0x00057DE6
	Public Function MaxDeployDistance(item As Global.Item) As Single
		Return 8F
	End Function

	' Token: 0x060007DC RID: 2012 RVA: 0x00059BED File Offset: 0x00057DED
	Public Function GetMinSpeed() As Single
		Return Me.GetSpeed(0F, 0F, 1F)
	End Function

	' Token: 0x060007DD RID: 2013 RVA: 0x00059C04 File Offset: 0x00057E04
	Public Function GetMaxSpeed() As Single
		Return Me.GetSpeed(1F, 0F, 0F)
	End Function

	' Token: 0x060007DE RID: 2014 RVA: 0x00059C1C File Offset: 0x00057E1C
	Public Function GetSpeed(running As Single, ducking As Single, crawling As Single) As Single
		Dim num As Single = 1F
		num -= Me.clothingMoveSpeedReduction
		If Me.IsSwimming() Then
			num += Me.clothingWaterSpeedBonus
		End If
		If crawling > 0F Then
			Return Mathf.Lerp(2.8F, 0.72F, crawling) * num
		End If
		Return Mathf.Lerp(Mathf.Lerp(2.8F, 5.5F, running), 1.7F, ducking) * num * Me.weaponMoveSpeedScale
	End Function

	' Token: 0x060007DF RID: 2015 RVA: 0x00059C88 File Offset: 0x00057E88
	Public Overrides Sub OnAttacked(info As HitInfo)
		Dim health As Single = MyBase.health
		If Me.InSafeZone() AndAlso Not Me.IsHostile() AndAlso info.Initiator IsNot Nothing AndAlso info.Initiator IsNot Me Then
			info.damageTypes.ScaleAll(0F)
		End If
		If MyBase.isServer Then
			Dim boneArea As HitArea = info.boneArea
			If boneArea <> CType((-1), HitArea) Then
				Dim list As List(Of Global.Item) = Facepunch.Pool.GetList(Of Global.Item)()
				list.AddRange(Me.inventory.containerWear.itemList)
				For i As Integer = 0 To list.Count - 1
					Dim item As Global.Item = list(i)
					If item IsNot Nothing Then
						Dim component As ItemModWearable = item.info.GetComponent(Of ItemModWearable)()
						If Not(component Is Nothing) AndAlso component.ProtectsArea(boneArea) Then
							item.OnAttacked(info)
						End If
					End If
				Next
				Facepunch.Pool.FreeList(Of Global.Item)(list)
				Me.inventory.ServerUpdate(0F)
			End If
		End If
		MyBase.OnAttacked(info)
		If MyBase.isServer AndAlso MyBase.isServer AndAlso info.hasDamage Then
			If Not info.damageTypes.Has(DamageType.Bleeding) AndAlso info.damageTypes.IsBleedCausing() AndAlso Not Me.IsWounded() AndAlso Not Me.IsImmortalTo(info) Then
				Me.metabolism.bleeding.Add(info.damageTypes.Total() * 0.2F)
			End If
			If Me.isMounted Then
				Me.GetMounted().MounteeTookDamage(Me, info)
			End If
			Me.CheckDeathCondition(info)
			If Me.net IsNot Nothing AndAlso Me.net.connection IsNot Nothing Then
				MyBase.ClientRPC(RpcTarget.Player("TakeDamageHit", Me))
			End If
			Dim a As String = StringPool.[Get](info.HitBone)
			Dim flag As Boolean = Vector3.Dot((info.PointEnd - info.PointStart).normalized, Me.eyes.BodyForward()) > 0.4F
			Dim initiatorPlayer As Global.BasePlayer = info.InitiatorPlayer
			If initiatorPlayer AndAlso Not info.damageTypes.IsMeleeType() Then
				initiatorPlayer.LifeStoryShotHit(info.Weapon)
			End If
			If info.isHeadshot Then
				If flag Then
					MyBase.SignalBroadcast(Global.BaseEntity.Signal.Flinch_RearHead, String.Empty, Nothing)
				Else
					MyBase.SignalBroadcast(Global.BaseEntity.Signal.Flinch_Head, String.Empty, Nothing)
				End If
				Effect.server.Run("assets/bundled/prefabs/fx/headshot.prefab", Me, 0UI, New Vector3(0F, 2F, 0F), Vector3.zero, If((initiatorPlayer IsNot Nothing), initiatorPlayer.net.connection, Nothing), False, Nothing)
				If Not initiatorPlayer Then
					GoTo IL_32A
				End If
				initiatorPlayer.stats.Add("headshot", 1, CType(5, Global.Stats))
				If Not initiatorPlayer.IsBeingSpectated Then
					GoTo IL_32A
				End If
				Using enumerator As List(Of Global.BaseEntity).Enumerator = initiatorPlayer.children.GetEnumerator()
					While enumerator.MoveNext()
						Dim baseEntity As Global.BaseEntity = enumerator.Current
						Dim basePlayer As Global.BasePlayer = TryCast(baseEntity, Global.BasePlayer)
						If basePlayer IsNot Nothing Then
							basePlayer.ClientRPC(RpcTarget.Player("SpectatedPlayerHeadshot", basePlayer))
						End If
					End While
					GoTo IL_32A
				End Using
			End If
			If flag Then
				MyBase.SignalBroadcast(Global.BaseEntity.Signal.Flinch_RearTorso, String.Empty, Nothing)
			ElseIf a = "spine" OrElse a = "spine2" Then
				MyBase.SignalBroadcast(Global.BaseEntity.Signal.Flinch_Stomach, String.Empty, Nothing)
			Else
				MyBase.SignalBroadcast(Global.BaseEntity.Signal.Flinch_Chest, String.Empty, Nothing)
			End If
		End If
		IL_32A:
		If Me.stats IsNot Nothing Then
			If Me.IsWounded() Then
				Me.stats.combat.LogAttack(info, "wounded", health)
			ElseIf Me.IsDead() Then
				Me.stats.combat.LogAttack(info, "killed", health)
			Else
				Me.stats.combat.LogAttack(info, "", health)
			End If
		End If
		If ConVar.[Global].cinematicGingerbreadCorpses Then
			info.HitMaterial = ConVar.[Global].GingerbreadMaterialID()
		End If
	End Sub

	' Token: 0x060007E0 RID: 2016 RVA: 0x0005A044 File Offset: 0x00058244
	Private Sub EnablePlayerCollider()
		If Me.playerCollider.enabled Then
			Return
		End If
		Me.RefreshColliderSize(True)
		Me.playerCollider.enabled = True
	End Sub

	' Token: 0x060007E1 RID: 2017 RVA: 0x0005A067 File Offset: 0x00058267
	Private Sub DisablePlayerCollider()
		If Not Me.playerCollider.enabled Then
			Return
		End If
		MyBase.RemoveFromTriggers()
		Me.playerCollider.enabled = False
	End Sub

	' Token: 0x060007E2 RID: 2018 RVA: 0x0005A08C File Offset: 0x0005828C
	Private Sub RefreshColliderSize(forced As Boolean)
		If Not forced Then
			If Not Me.playerCollider.enabled Then
				Return
			End If
			If UnityEngine.Time.time < Me.nextColliderRefreshTime Then
				Return
			End If
		End If
		Me.nextColliderRefreshTime = UnityEngine.Time.time + 0.25F + UnityEngine.Random.Range(-0.05F, 0.05F)
		Dim baseMountable As BaseMountable = Me.GetMounted()
		Dim customPlayerCollider As Global.BasePlayer.CapsuleColliderInfo
		If baseMountable IsNot Nothing AndAlso baseMountable.IsValid() Then
			If baseMountable.modifiesPlayerCollider Then
				customPlayerCollider = baseMountable.customPlayerCollider
			Else
				customPlayerCollider = Me.playerColliderStanding
			End If
		ElseIf Me.IsIncapacitated() OrElse Me.IsSleeping() Then
			customPlayerCollider = Me.playerColliderLyingDown
		ElseIf Me.IsCrawling() Then
			customPlayerCollider = Me.playerColliderCrawling
		ElseIf Me.modelState.ducked OrElse Me.IsSwimming() Then
			customPlayerCollider = Me.playerColliderDucked
		Else
			customPlayerCollider = Me.playerColliderStanding
		End If
		If Me.playerCollider.height <> customPlayerCollider.height OrElse Me.playerCollider.radius <> customPlayerCollider.radius OrElse Me.playerCollider.center <> customPlayerCollider.center Then
			Me.playerCollider.height = customPlayerCollider.height
			Me.playerCollider.radius = customPlayerCollider.radius
			Me.playerCollider.center = customPlayerCollider.center
		End If
	End Sub

	' Token: 0x060007E3 RID: 2019 RVA: 0x0005A1CB File Offset: 0x000583CB
	Private Sub SetPlayerRigidbodyState(isEnabled As Boolean)
		If isEnabled Then
			Me.AddPlayerRigidbody()
			Return
		End If
		Me.RemovePlayerRigidbody()
	End Sub

	' Token: 0x060007E4 RID: 2020 RVA: 0x0005A1E0 File Offset: 0x000583E0
	Private Sub AddPlayerRigidbody()
		If Me.playerRigidbody Is Nothing Then
			Me.playerRigidbody = MyBase.gameObject.GetComponent(Of Rigidbody)()
		End If
		If Me.playerRigidbody Is Nothing Then
			Me.playerRigidbody = MyBase.gameObject.AddComponent(Of Rigidbody)()
			Me.playerRigidbody.useGravity = False
			Me.playerRigidbody.isKinematic = True
			Me.playerRigidbody.mass = 1F
			Me.playerRigidbody.interpolation = RigidbodyInterpolation.None
			Me.playerRigidbody.collisionDetectionMode = CollisionDetectionMode.Discrete
		End If
	End Sub

	' Token: 0x060007E5 RID: 2021 RVA: 0x0005A26C File Offset: 0x0005846C
	Private Sub RemovePlayerRigidbody()
		If Me.playerRigidbody Is Nothing Then
			Me.playerRigidbody = MyBase.gameObject.GetComponent(Of Rigidbody)()
		End If
		If Me.playerRigidbody IsNot Nothing Then
			MyBase.RemoveFromTriggers()
			UnityEngine.[Object].DestroyImmediate(Me.playerRigidbody)
			Me.playerRigidbody = Nothing
		End If
	End Sub

	' Token: 0x060007E6 RID: 2022 RVA: 0x0005A2C0 File Offset: 0x000584C0
	Public Function IsEnsnared() As Boolean
		If Me.triggers Is Nothing Then
			Return False
		End If
		For i As Integer = 0 To Me.triggers.Count - 1
			If TypeOf Me.triggers(i)Is TriggerEnsnare Then
				Return True
			End If
		Next
		Return False
	End Function

	' Token: 0x060007E7 RID: 2023 RVA: 0x0005A304 File Offset: 0x00058504
	Public Function IsAttacking() As Boolean
		Dim heldEntity As Global.HeldEntity = Me.GetHeldEntity()
		If heldEntity Is Nothing Then
			Return False
		End If
		Dim attackEntity As AttackEntity = TryCast(heldEntity, AttackEntity)
		Return Not(attackEntity Is Nothing) AndAlso attackEntity.NextAttackTime - UnityEngine.Time.time > attackEntity.repeatDelay - 1F
	End Function

	' Token: 0x060007E8 RID: 2024 RVA: 0x0005A350 File Offset: 0x00058550
	Public Function CanAttack() As Boolean
		Dim heldEntity As Global.HeldEntity = Me.GetHeldEntity()
		If heldEntity Is Nothing Then
			Return False
		End If
		Dim flag As Boolean = Me.IsSwimming()
		Dim flag2 As Boolean = heldEntity.CanBeUsedInWater()
		Return Not Me.modelState.onLadder AndAlso (flag OrElse Me.modelState.onground) AndAlso (Not flag OrElse flag2) AndAlso Not Me.IsEnsnared()
	End Function

	' Token: 0x060007E9 RID: 2025 RVA: 0x0005A3B1 File Offset: 0x000585B1
	Public Function OnLadder() As Boolean
		Return Me.modelState.onLadder AndAlso Not Me.IsWounded() AndAlso MyBase.FindTrigger(Of TriggerLadder)()
	End Function

	' Token: 0x060007EA RID: 2026 RVA: 0x0005A3D5 File Offset: 0x000585D5
	Public Function IsSwimming() As Boolean
		Return Me.WaterFactor() >= 0.65F
	End Function

	' Token: 0x060007EB RID: 2027 RVA: 0x0005A3E7 File Offset: 0x000585E7
	Public Function IsHeadUnderwater() As Boolean
		Return Me.WaterFactor() > 0.75F
	End Function

	' Token: 0x060007EC RID: 2028 RVA: 0x0005A3F6 File Offset: 0x000585F6
	Public Overridable Function IsOnGround() As Boolean
		Return Me.modelState.onground
	End Function

	' Token: 0x060007ED RID: 2029 RVA: 0x0005A403 File Offset: 0x00058603
	Public Function IsRunning() As Boolean
		Return Me.modelState IsNot Nothing AndAlso Me.modelState.sprinting
	End Function

	' Token: 0x060007EE RID: 2030 RVA: 0x0005A41A File Offset: 0x0005861A
	Public Function IsDucked() As Boolean
		Return Me.modelState IsNot Nothing AndAlso Me.modelState.ducked
	End Function

	' Token: 0x060007EF RID: 2031 RVA: 0x0005A431 File Offset: 0x00058631
	Public Sub ShowToast(style As GameTip.Styles, phrase As Translate.Phrase, ParamArray arguments As String())
		If MyBase.isServer Then
			Me.SendConsoleCommand("gametip.showtoast_translated", New Object() { CInt(style), phrase.token, phrase.english, arguments })
			Return
		End If
	End Sub

	' Token: 0x060007F0 RID: 2032 RVA: 0x0005A46C File Offset: 0x0005866C
	Public Sub ChatMessage(msg As String)
		If MyBase.isServer Then
			Me.SendConsoleCommand("chat.add", New Object() { 2, 0, msg })
			Return
		End If
	End Sub

	' Token: 0x060007F1 RID: 2033 RVA: 0x0005A49E File Offset: 0x0005869E
	Public Sub ConsoleMessage(msg As String)
		If MyBase.isServer Then
			Me.SendConsoleCommand("echo " + msg, Array.Empty(Of Object)())
			Return
		End If
	End Sub

	' Token: 0x060007F2 RID: 2034 RVA: 0x0005A4BF File Offset: 0x000586BF
	Public Overrides Function PenetrationResistance(info As HitInfo) As Single
		Return 100F
	End Function

	' Token: 0x060007F3 RID: 2035 RVA: 0x0005A4C8 File Offset: 0x000586C8
	Public Overrides Sub ScaleDamage(info As HitInfo)
		If Me.isMounted Then
			Me.GetMounted().ScaleDamageForPlayer(Me, info)
		End If
		If info.UseProtection Then
			Dim boneArea As HitArea = info.boneArea
			If boneArea <> CType((-1), HitArea) Then
				Me.cachedProtection.Clear()
				Me.cachedProtection.Add(Me.inventory.containerWear.itemList, boneArea)
				Me.cachedProtection.Multiply(DamageType.Arrow, ConVar.Server.arrowarmor)
				Me.cachedProtection.Multiply(DamageType.Bullet, ConVar.Server.bulletarmor)
				Me.cachedProtection.Multiply(DamageType.Slash, ConVar.Server.meleearmor)
				Me.cachedProtection.Multiply(DamageType.Blunt, ConVar.Server.meleearmor)
				Me.cachedProtection.Multiply(DamageType.Stab, ConVar.Server.meleearmor)
				Me.cachedProtection.Multiply(DamageType.Bleeding, ConVar.Server.bleedingarmor)
				Me.cachedProtection.Scale(info.damageTypes, 1F)
			Else
				Me.baseProtection.Scale(info.damageTypes, 1F)
			End If
		End If
		If info.damageProperties Then
			info.damageProperties.ScaleDamage(info)
		End If
	End Sub

	' Token: 0x060007F4 RID: 2036 RVA: 0x0005A5DC File Offset: 0x000587DC
	Public Sub ResetWeaponMoveSpeedScale()
		Me.weaponMoveSpeedScale = 1F
	End Sub

	' Token: 0x060007F5 RID: 2037 RVA: 0x0005A5EC File Offset: 0x000587EC
	Private Sub UpdateMoveSpeedFromClothing()
		Dim num As Single = 0F
		Dim num2 As Single = 0F
		Dim num3 As Single = 0F
		Dim flag As Boolean = False
		Dim flag2 As Boolean = False
		Dim num4 As Single = 0F
		Me.eggVision = 0F
		MyBase.Weight = 0F
		For Each item As Global.Item In Me.inventory.containerWear.itemList
			Dim component As ItemModWearable = item.info.GetComponent(Of ItemModWearable)()
			If component Then
				If component.blocksAiming Then
					flag = True
				End If
				If component.blocksEquipping Then
					flag2 = True
				End If
				num4 += component.accuracyBonus
				Me.eggVision += component.eggVision
				MyBase.Weight += component.weight
				If component.movementProperties IsNot Nothing Then
					num2 += component.movementProperties.speedReduction
					num = Mathf.Max(num, component.movementProperties.minSpeedReduction)
					num3 += component.movementProperties.waterSpeedBonus
				End If
			End If
		Next
		Me.clothingAccuracyBonus = num4
		Me.clothingMoveSpeedReduction = Mathf.Max(num2, num)
		Me.clothingBlocksAiming = flag
		Me.clothingWaterSpeedBonus = num3
		Me.equippingBlocked = flag2
		If MyBase.isServer AndAlso Me.equippingBlocked Then
			Me.UpdateActiveItem(Nothing)
		End If
	End Sub

	' Token: 0x060007F6 RID: 2038 RVA: 0x0005A76C File Offset: 0x0005896C
	Public Overridable Sub UpdateProtectionFromClothing()
		Me.baseProtection.Clear()
		Me.baseProtection.Add(Me.inventory.containerWear.itemList, CType((-1), HitArea))
		Dim num As Single = 0.16666667F
		For i As Integer = 0 To Me.baseProtection.amounts.Length - 1
			If i <> 17 Then
				If i = 22 Then
					Me.baseProtection.amounts(i) = 1F
				Else
					Me.baseProtection.amounts(i) *= num
				End If
			End If
		Next
	End Sub

	' Token: 0x060007F7 RID: 2039 RVA: 0x0005A7F2 File Offset: 0x000589F2
	Public Overrides Function Categorize() As String
		Return "player"
	End Function

	' Token: 0x060007F8 RID: 2040 RVA: 0x0005A7FC File Offset: 0x000589FC
	Public Overrides Function ToString() As String
		If Me._name Is Nothing Then
			If MyBase.isServer Then
				Me._name = String.Format("{0}[{1}]", Me.displayName, Me.userID)
			Else
				Me._name = MyBase.ShortPrefabName
			End If
		End If
		Return Me._name
	End Function

	' Token: 0x060007F9 RID: 2041 RVA: 0x0005A850 File Offset: 0x00058A50
	Public Function GetDebugStatus() As String
		Dim stringBuilder As StringBuilder = New StringBuilder()
		stringBuilder.AppendFormat("Entity: {0}" & vbLf, Me.ToString())
		stringBuilder.AppendFormat("Name: {0}" & vbLf, Me.displayName)
		stringBuilder.AppendFormat("SteamID: {0}" & vbLf, Me.userID)
		For Each obj As Object In [Enum].GetValues(GetType(Global.BasePlayer.PlayerFlags))
			Dim playerFlags As Global.BasePlayer.PlayerFlags = CType(obj, Global.BasePlayer.PlayerFlags)
			stringBuilder.AppendFormat("{1}: {0}" & vbLf, Me.HasPlayerFlag(playerFlags), playerFlags)
		Next
		Return stringBuilder.ToString()
	End Function

	' Token: 0x060007FA RID: 2042 RVA: 0x0005A910 File Offset: 0x00058B10
	Public Overrides Function GetItem(itemId As ItemId) As Global.Item
		If Me.inventory Is Nothing Then
			Return Nothing
		End If
		Return Me.inventory.FindItemByUID(itemId)
	End Function

	' Token: 0x170000EC RID: 236
	' (get) Token: 0x060007FB RID: 2043 RVA: 0x0005A92E File Offset: 0x00058B2E
	Public Overrides ReadOnly Property Traits As Global.BaseEntity.TraitFlag
		Get
			Return MyBase.Traits Or Global.BaseEntity.TraitFlag.Human Or Global.BaseEntity.TraitFlag.Food Or Global.BaseEntity.TraitFlag.Meat Or Global.BaseEntity.TraitFlag.Alive
		End Get
	End Property

	' Token: 0x060007FC RID: 2044 RVA: 0x0005A940 File Offset: 0x00058B40
	Public Overrides Function WaterFactor() As Single
		If Me.GetMounted().IsValid() Then
			Return Me.GetMounted().WaterFactorForPlayer(Me)
		End If
		If MyBase.GetParentEntity() IsNot Nothing AndAlso MyBase.GetParentEntity().BlocksWaterFor(Me) Then
			Return 0F
		End If
		Dim radius As Single = Me.playerCollider.radius
		Dim num As Single = Me.playerCollider.height * 0.5F
		Dim start As Vector3 = Me.playerCollider.transform.position + Me.playerCollider.transform.rotation * (Me.playerCollider.center - Vector3.up * (num - radius))
		Dim [end] As Vector3 = Me.playerCollider.transform.position + Me.playerCollider.transform.rotation * (Me.playerCollider.center + Vector3.up * (num - radius))
		Return WaterLevel.Factor(start, [end], radius, True, True, Me)
	End Function

	' Token: 0x060007FD RID: 2045 RVA: 0x0005AA40 File Offset: 0x00058C40
	Public Overrides Function AirFactor() As Single
		Dim num As Single = If((Me.WaterFactor() > 0.85F), 0F, 1F)
		Dim baseMountable As BaseMountable = Me.GetMounted()
		If baseMountable.IsValid() AndAlso baseMountable.BlocksWaterFor(Me) Then
			Dim num2 As Single = baseMountable.AirFactor()
			If num2 < num Then
				num = num2
			End If
		End If
		Return num
	End Function

	' Token: 0x060007FE RID: 2046 RVA: 0x0005AA90 File Offset: 0x00058C90
	Public Function GetOxygenTime(<System.Runtime.InteropServices.OutAttribute()> ByRef airSupplyType As ItemModGiveOxygen.AirSupplyType) As Single
		Dim mountedVehicle As Global.BaseVehicle = Me.GetMountedVehicle()
		If mountedVehicle.IsValid() Then
			Dim airSupply As IAirSupply = TryCast(mountedVehicle, IAirSupply)
			If airSupply IsNot Nothing Then
				Dim airTimeRemaining As Single = airSupply.GetAirTimeRemaining()
				If airTimeRemaining > 0F Then
					airSupplyType = airSupply.AirType
					Return airTimeRemaining
				End If
			End If
		End If
		For Each item As Global.Item In Me.inventory.containerWear.itemList
			Dim componentInChildren As IAirSupply = item.info.GetComponentInChildren(Of IAirSupply)()
			If componentInChildren IsNot Nothing Then
				Dim airTimeRemaining2 As Single = componentInChildren.GetAirTimeRemaining()
				If airTimeRemaining2 > 0F Then
					airSupplyType = componentInChildren.AirType
					Return airTimeRemaining2
				End If
			End If
		Next
		airSupplyType = ItemModGiveOxygen.AirSupplyType.Lungs
		If Me.metabolism.oxygen.value > 0.5F Then
			Dim num As Single = 5F
			Dim num2 As Single = Mathf.InverseLerp(0.5F, 1F, Me.metabolism.oxygen.value)
			Return num * num2
		End If
		Return 0F
	End Function

	' Token: 0x060007FF RID: 2047 RVA: 0x0005AB94 File Offset: 0x00058D94
	Public Overrides Function ShouldInheritNetworkGroup() As Boolean
		Return Me.IsSpectating()
	End Function

	' Token: 0x06000800 RID: 2048 RVA: 0x0005AB9C File Offset: 0x00058D9C
	Public Shared Function AnyPlayersVisibleToEntity(pos As Vector3, radius As Single, source As Global.BaseEntity, entityEyePos As Vector3, Optional ignorePlayersWithPriv As Boolean = False) As Boolean
		Dim list As List(Of RaycastHit) = Facepunch.Pool.GetList(Of RaycastHit)()
		Dim list2 As List(Of Global.BasePlayer) = Facepunch.Pool.GetList(Of Global.BasePlayer)()
		Global.Vis.Entities(Of Global.BasePlayer)(pos, radius, list2, 131072, QueryTriggerInteraction.Collide)
		Dim flag As Boolean = False
		For Each basePlayer As Global.BasePlayer In list2
			If Not basePlayer.IsSleeping() AndAlso basePlayer.IsAlive() AndAlso (Not basePlayer.IsBuildingAuthed() OrElse Not ignorePlayersWithPriv) Then
				list.Clear()
				GamePhysics.TraceAll(New Ray(basePlayer.eyes.position, (entityEyePos - basePlayer.eyes.position).normalized), 0F, list, 9F, 1218519297, QueryTriggerInteraction.UseGlobal, Nothing)
				For i As Integer = 0 To list.Count - 1
					Dim entity As Global.BaseEntity = list(i).GetEntity()
					If entity IsNot Nothing AndAlso (entity Is source OrElse entity.EqualNetID(source)) Then
						flag = True
						Exit For
					End If
					If Not(entity IsNot Nothing) OrElse entity.ShouldBlockProjectiles() Then
						Exit For
					End If
				Next
				If flag Then
					Exit For
				End If
			End If
		Next
		Facepunch.Pool.FreeList(Of RaycastHit)(list)
		Facepunch.Pool.FreeList(Of Global.BasePlayer)(list2)
		Return flag
	End Function

	' Token: 0x06000801 RID: 2049 RVA: 0x0005ACE4 File Offset: 0x00058EE4
	Public Function IsStandingOnEntity(standingOn As Global.BaseEntity, layerMask As Integer) As Boolean
		If Not Me.IsOnGround() Then
			Return False
		End If
		Dim hit As RaycastHit
		If UnityEngine.Physics.SphereCast(MyBase.transform.position + Vector3.up * (0.25F + Me.GetRadius()), Me.GetRadius() * 0.95F, Vector3.down, hit, 4F, layerMask) Then
			Dim entity As Global.BaseEntity = hit.GetEntity()
			If entity IsNot Nothing Then
				If entity.EqualNetID(standingOn) Then
					Return True
				End If
				Dim parentEntity As Global.BaseEntity = entity.GetParentEntity()
				If parentEntity IsNot Nothing AndAlso parentEntity.EqualNetID(standingOn) Then
					Return True
				End If
			End If
		End If
		Return False
	End Function

	' Token: 0x06000802 RID: 2050 RVA: 0x0005AD78 File Offset: 0x00058F78
	Public Sub SetActiveTelephone(t As PhoneController)
		Me.activeTelephone = t
	End Sub

	' Token: 0x170000ED RID: 237
	' (get) Token: 0x06000803 RID: 2051 RVA: 0x0005AD81 File Offset: 0x00058F81
	Public ReadOnly Property HasActiveTelephone As Boolean
		Get
			Return Me.activeTelephone IsNot Nothing
		End Get
	End Property

	' Token: 0x170000EE RID: 238
	' (get) Token: 0x06000804 RID: 2052 RVA: 0x0005AD8F File Offset: 0x00058F8F
	Public ReadOnly Property IsDesigningAI As Boolean
		Get
			Return Me.designingAIEntity IsNot Nothing
		End Get
	End Property

	' Token: 0x06000805 RID: 2053 RVA: 0x0005ADA0 File Offset: 0x00058FA0
	Public Sub ClearDesigningAIEntity()
		If Me.IsDesigningAI Then
			Dim component As IAIDesign = Me.designingAIEntity.GetComponent(Of IAIDesign)()
			If component IsNot Nothing Then
				component.StopDesigning()
			End If
		End If
		Me.designingAIEntity = Nothing
	End Sub

	' Token: 0x06000808 RID: 2056 RVA: 0x0005B1AC File Offset: 0x000593AC
	<CompilerGenerated()>
	Private Function <CountWaveTargets>g__CheckPlayer|118_0(player As Global.BasePlayer, ByRef A_2 As Global.BasePlayer.<>c__DisplayClass118_0) As Boolean
		Return Not(player Is Nothing) AndAlso Not(player Is Me) AndAlso player.SqrDistance(A_2.position) <= A_2.sqrDistance AndAlso Vector3.Dot((player.transform.position - A_2.position).normalized, A_2.forward) >= A_2.minimumDot AndAlso Not A_2.workingList.Contains(player.net.ID)
	End Function

	' Token: 0x06000809 RID: 2057 RVA: 0x0005B234 File Offset: 0x00059434
	<CompilerGenerated()>
	Private Function <FindUnusedPointOfInterestColour>g__HasColour|149_0(index As Integer) As Boolean
		Using enumerator As List(Of MapNote).Enumerator = Me.State.pointsOfInterest.GetEnumerator()
			While enumerator.MoveNext()
				If enumerator.Current.colourIndex = index Then
					Return True
				End If
			End While
		End Using
		Return False
	End Function

	' Token: 0x0600080A RID: 2058 RVA: 0x0005B294 File Offset: 0x00059494
	<CompilerGenerated()>
	Private Function <SaveSecondaryData>g__GetPoolableMugshotData|212_0(relationshipInfo As Global.RelationshipManager.PlayerRelationshipInfo) As ArraySegment(Of Byte)
		Dim arraySegment As ArraySegment(Of Byte)
		If relationshipInfo.mugshotCrc = 0UI Then
			arraySegment = Nothing
			Return arraySegment
		End If
		Try
			Dim steamIdHash As UInteger = Global.RelationshipManager.GetSteamIdHash(Me.userID, relationshipInfo.player)
			Dim array As Byte() = FileStorage.server.[Get](relationshipInfo.mugshotCrc, FileStorage.Type.jpg, Global.RelationshipManager.ServerInstance.net.ID, steamIdHash)
			If array Is Nothing Then
				arraySegment = Nothing
				arraySegment = arraySegment
			Else
				Dim array2 As Byte() = System.Buffers.ArrayPool(Of Byte).[Shared].Rent(array.Length)
				New Span(Of Byte)(array).CopyTo(array2)
				arraySegment = New ArraySegment(Of Byte)(array2, 0, array.Length)
			End If
		Catch exception As Exception
			Debug.LogException(exception)
			arraySegment = Nothing
		End Try
		Return arraySegment
	End Function

	' Token: 0x0600080B RID: 2059 RVA: 0x0005B350 File Offset: 0x00059550
	<CompilerGenerated()>
	Private Sub <SendRespawnOptions>g__CollectExternalAndSend|409_0()
		Dim <<SendRespawnOptions>g__CollectExternalAndSend|409_0>d As Global.BasePlayer.<<SendRespawnOptions>g__CollectExternalAndSend|409_0>d
		<<SendRespawnOptions>g__CollectExternalAndSend|409_0>d.<>t__builder = AsyncVoidMethodBuilder.Create()
		<<SendRespawnOptions>g__CollectExternalAndSend|409_0>d.<>4__this = Me
		<<SendRespawnOptions>g__CollectExternalAndSend|409_0>d.<>1__state = -1
		<<SendRespawnOptions>g__CollectExternalAndSend|409_0>d.<>t__builder.Start(Of Global.BasePlayer.<<SendRespawnOptions>g__CollectExternalAndSend|409_0>d)(<<SendRespawnOptions>g__CollectExternalAndSend|409_0>d)
	End Sub

	' Token: 0x0600080C RID: 2060 RVA: 0x0005B388 File Offset: 0x00059588
	<CompilerGenerated()>
	Private Sub <SendRespawnOptions>g__SendToPlayer|409_1(spawnOptions As List(Of RespawnInformation.SpawnOptions), loading As Boolean)
		Using respawnInformation As RespawnInformation = Facepunch.Pool.[Get](Of RespawnInformation)()
			respawnInformation.spawnOptions = spawnOptions
			respawnInformation.loading = loading
			If ConVar.Server.max_shelters = Global.LegacyShelter.FpShelterDefault AndAlso Global.LegacyShelter.SheltersPerPlayer.ContainsKey(Me.userID) AndAlso Global.LegacyShelter.SheltersPerPlayer(Me.userID).Count > 0 Then
				respawnInformation.shelterPositions = Facepunch.Pool.GetList(Of Vector3)()
				For Each legacyShelter As Global.LegacyShelter In Global.LegacyShelter.SheltersPerPlayer(Me.userID)
					respawnInformation.shelterPositions.Add(legacyShelter.transform.position)
				Next
			End If
			If Me.IsDead() Then
				respawnInformation.previousLife = Me.previousLifeStory
				If Not ConVar.Server.skipDeathScreenFade Then
					respawnInformation.fadeIn = (Me.previousLifeStory IsNot Nothing AndAlso CULng(Me.previousLifeStory.timeDied) > CULng(CLng((Epoch.Current - 5))))
				Else
					respawnInformation.fadeIn = False
				End If
			End If
			MyBase.ClientRPC(Of RespawnInformation)(RpcTarget.Player("OnRespawnInformation", Me), respawnInformation)
		End Using
	End Sub

	' Token: 0x0600080D RID: 2061 RVA: 0x0005B4E8 File Offset: 0x000596E8
	<CompilerGenerated()>
	Friend Shared Function <CreateCorpse>g__GetFloatBasedOnUserID|439_0(steamid As ULong, seed As ULong) As Single
		Dim state As UnityEngine.Random.State = UnityEngine.Random.state
		UnityEngine.Random.InitState(CInt((seed + steamid)))
		Dim result As Single = UnityEngine.Random.Range(0F, 1F)
		UnityEngine.Random.state = state
		Return result
	End Function

	' Token: 0x0600080E RID: 2062 RVA: 0x0005B51C File Offset: 0x0005971C
	<CompilerGenerated()>
	Friend Shared Sub <OcclusionPlayerFound>g__UpdateVisibility|498_0(src As Global.BasePlayer, dst As Global.BasePlayer)
		If Not src.lastPlayerVisibility.ContainsKey(dst) AndAlso src.net.connection IsNot Nothing Then
			dst.SendAsSnapshot(src.net.connection, False)
			For Each baseEntity As Global.BaseEntity In dst.children
				baseEntity.SendAsSnapshot(src.net.connection, False)
			Next
		End If
		src.lastPlayerVisibility(dst) = src.GetNetworkTime()
	End Sub

	' Token: 0x0600080F RID: 2063 RVA: 0x0005B5B8 File Offset: 0x000597B8
	<CompilerGenerated()>
	Friend Shared Sub <OcclusionPlayerLost>g__UpdateVisibility|499_0(src As Global.BasePlayer, dst As Global.BasePlayer)
		If src.lastPlayerVisibility.Remove(dst) AndAlso src.net.connection IsNot Nothing Then
			dst.DestroyOnClient(src.net.connection)
		End If
	End Sub

	' Token: 0x04000425 RID: 1061
	<NonSerialized()>
	Public isInAir As Boolean

	' Token: 0x04000426 RID: 1062
	<NonSerialized()>
	Public isOnPlayer As Boolean

	' Token: 0x04000427 RID: 1063
	<NonSerialized()>
	Public violationLevel As Single

	' Token: 0x04000428 RID: 1064
	<NonSerialized()>
	Public lastViolationTime As Single

	' Token: 0x04000429 RID: 1065
	<NonSerialized()>
	Public lastAdminCheatTime As Single

	' Token: 0x0400042A RID: 1066
	<NonSerialized()>
	Public lastViolationType As AntiHackType

	' Token: 0x0400042B RID: 1067
	<NonSerialized()>
	Public vehiclePauseTime As Single

	' Token: 0x0400042C RID: 1068
	<NonSerialized()>
	Public speedhackPauseTime As Single

	' Token: 0x0400042D RID: 1069
	<NonSerialized()>
	Public speedhackDistance As Single

	' Token: 0x0400042E RID: 1070
	<NonSerialized()>
	Public flyhackPauseTime As Single

	' Token: 0x0400042F RID: 1071
	<NonSerialized()>
	Public flyhackDistanceVertical As Single

	' Token: 0x04000430 RID: 1072
	<NonSerialized()>
	Public flyhackDistanceHorizontal As Single

	' Token: 0x04000431 RID: 1073
	<NonSerialized()>
	Public lastGroundedPosition As Vector3

	' Token: 0x04000432 RID: 1074
	<NonSerialized()>
	Public fallingVelocity As Single

	' Token: 0x04000433 RID: 1075
	<NonSerialized()>
	Public fallingDistance As Single

	' Token: 0x04000434 RID: 1076
	<NonSerialized()>
	Public timeInAir As Single

	' Token: 0x04000435 RID: 1077
	<NonSerialized()>
	Public waterDelay As Single

	' Token: 0x04000436 RID: 1078
	<NonSerialized()>
	Public initialVelocity As Vector3

	' Token: 0x04000437 RID: 1079
	<NonSerialized()>
	Public rpcHistory As TimeAverageValueLookup(Of UInteger) = New TimeAverageValueLookup(Of UInteger)()

	' Token: 0x04000438 RID: 1080
	Public Shared ClanInviteSuccess As Translate.Phrase = New Translate.Phrase("clan.action.invite.success", "Invited {name} to your clan.")

	' Token: 0x04000439 RID: 1081
	Public Shared ClanInviteFailure As Translate.Phrase = New Translate.Phrase("clan.action.invite.failure", "Failed to invite {name} to your clan. Please wait a minute and try again.")

	' Token: 0x0400043A RID: 1082
	Public Shared ClanInviteFull As Translate.Phrase = New Translate.Phrase("clan.action.invite.full", "Cannot invite {name} to your clan because your clan is full.")

	' Token: 0x0400043B RID: 1083
	<NonSerialized()>
	Public clanId As Long

	' Token: 0x0400043C RID: 1084
	<NonSerialized()>
	Public serverClan As IClan

	' Token: 0x0400043D RID: 1085
	Public GestureViewModel As ViewModel

	' Token: 0x0400043E RID: 1086
	Private Const drinkRange As Single = 1.5F

	' Token: 0x0400043F RID: 1087
	Private Const drinkMovementSpeed As Single = 0.1F

	' Token: 0x04000440 RID: 1088
	<NonSerialized()>
	Private networkQueue As Global.BasePlayer.NetworkQueueList() = New Global.BasePlayer.NetworkQueueList() { New Global.BasePlayer.NetworkQueueList(), New Global.BasePlayer.NetworkQueueList() }

	' Token: 0x04000441 RID: 1089
	<NonSerialized()>
	Private SnapshotQueue As Global.BasePlayer.NetworkQueueList = New Global.BasePlayer.NetworkQueueList()

	' Token: 0x04000442 RID: 1090
	Public Const GestureCancelString As String = "cancel"

	' Token: 0x04000443 RID: 1091
	Public gestureList As GestureCollection

	' Token: 0x04000444 RID: 1092
	Private gestureFinishedTime As TimeUntil

	' Token: 0x04000445 RID: 1093
	Private blockHeldInputTimer As TimeSince

	' Token: 0x04000446 RID: 1094
	Private currentGesture As GestureConfig

	' Token: 0x04000447 RID: 1095
	Private recentWaveTargets As HashSet(Of NetworkableId) = New HashSet(Of NetworkableId)()

	' Token: 0x04000448 RID: 1096
	Public Const WAVED_PLAYERS_STAT As String = "waved_at_players"

	' Token: 0x04000449 RID: 1097
	Public currentTeam As ULong

	' Token: 0x0400044A RID: 1098
	Public Shared MaxTeamSizeToast As Translate.Phrase = New Translate.Phrase("maxteamsizetip", "Your team is full. Remove a member to invite another player.")

	' Token: 0x0400044B RID: 1099
	Private sentInstrumentTeamAchievement As Boolean

	' Token: 0x0400044C RID: 1100
	Private sentSummerTeamAchievement As Boolean

	' Token: 0x0400044D RID: 1101
	Private Const TEAMMATE_INSTRUMENT_COUNT_ACHIEVEMENT As Integer = 4

	' Token: 0x0400044E RID: 1102
	Private Const TEAMMATE_SUMMER_FLOATING_COUNT_ACHIEVEMENT As Integer = 4

	' Token: 0x0400044F RID: 1103
	Private Const TEAMMATE_INSTRUMENT_ACHIEVEMENT As String = "TEAM_INSTRUMENTS"

	' Token: 0x04000450 RID: 1104
	Private Const TEAMMATE_SUMMER_ACHIEVEMENT As String = "SUMMER_INFLATABLE"

	' Token: 0x04000451 RID: 1105
	Public Shared MarkerLimitPhrase As Translate.Phrase = New Translate.Phrase("map.marker.limited", "Cannot place more than {0} markers.")

	' Token: 0x04000452 RID: 1106
	Public Const MaxMapNoteLabelLength As Integer = 10

	' Token: 0x04000453 RID: 1107
	Public missions As List(Of BaseMission.MissionInstance) = New List(Of BaseMission.MissionInstance)()

	' Token: 0x04000454 RID: 1108
	Private thinkEvery As Single = 1F

	' Token: 0x04000455 RID: 1109
	Private timeSinceMissionThink As Single

	' Token: 0x04000456 RID: 1110
	Private followupMission As BaseMission

	' Token: 0x04000457 RID: 1111
	Private followupMissionProvider As IMissionProvider

	' Token: 0x04000458 RID: 1112
	Private _activeMission As Integer = -1

	' Token: 0x04000459 RID: 1113
	<NonSerialized()>
	Public modelState As ModelState = New ModelState()

	' Token: 0x0400045B RID: 1115
	<NonSerialized()>
	Private wantsSendModelState As Boolean

	' Token: 0x0400045C RID: 1116
	<NonSerialized()>
	Private nextModelStateUpdate As Single

	' Token: 0x0400045D RID: 1117
	<NonSerialized()>
	Private mounted As EntityRef

	' Token: 0x0400045E RID: 1118
	Private nextSeatSwapTime As Single

	' Token: 0x0400045F RID: 1119
	Public PetEntity As Global.BaseEntity

	' Token: 0x04000460 RID: 1120
	<NonSerialized()>
	Public Pet As IPet

	' Token: 0x04000461 RID: 1121
	Private lastPetCommandIssuedTime As Single

	' Token: 0x04000462 RID: 1122
	Private Shared HostileTitle As Translate.Phrase = New Translate.Phrase("ping_hostile", "Hostile")

	' Token: 0x04000463 RID: 1123
	Private Shared HostileDesc As Translate.Phrase = New Translate.Phrase("ping_hostile_desc", "Danger in area")

	' Token: 0x04000464 RID: 1124
	Private Shared HostileMarker As Global.BasePlayer.PingStyle = New Global.BasePlayer.PingStyle(4, 3, Global.BasePlayer.HostileTitle, Global.BasePlayer.HostileDesc, Global.BasePlayer.PingType.Hostile)

	' Token: 0x04000465 RID: 1125
	Private Shared GoToTitle As Translate.Phrase = New Translate.Phrase("ping_goto", "Go To")

	' Token: 0x04000466 RID: 1126
	Private Shared GoToDesc As Translate.Phrase = New Translate.Phrase("ping_goto_desc", "Look at this")

	' Token: 0x04000467 RID: 1127
	Private Shared GoToMarker As Global.BasePlayer.PingStyle = New Global.BasePlayer.PingStyle(0, 2, Global.BasePlayer.GoToTitle, Global.BasePlayer.GoToDesc, Global.BasePlayer.PingType.[GoTo])

	' Token: 0x04000468 RID: 1128
	Private Shared DollarTitle As Translate.Phrase = New Translate.Phrase("ping_dollar", "Value")

	' Token: 0x04000469 RID: 1129
	Private Shared DollarDesc As Translate.Phrase = New Translate.Phrase("ping_dollar_desc", "Something valuable is here")

	' Token: 0x0400046A RID: 1130
	Private Shared DollarMarker As Global.BasePlayer.PingStyle = New Global.BasePlayer.PingStyle(1, 1, Global.BasePlayer.DollarTitle, Global.BasePlayer.DollarDesc, Global.BasePlayer.PingType.Dollar)

	' Token: 0x0400046B RID: 1131
	Private Shared LootTitle As Translate.Phrase = New Translate.Phrase("ping_loot", "Loot")

	' Token: 0x0400046C RID: 1132
	Private Shared LootDesc As Translate.Phrase = New Translate.Phrase("ping_loot_desc", "Loot is here")

	' Token: 0x0400046D RID: 1133
	Private Shared LootMarker As Global.BasePlayer.PingStyle = New Global.BasePlayer.PingStyle(11, 0, Global.BasePlayer.LootTitle, Global.BasePlayer.LootDesc, Global.BasePlayer.PingType.Loot)

	' Token: 0x0400046E RID: 1134
	Private Shared NodeTitle As Translate.Phrase = New Translate.Phrase("ping_node", "Node")

	' Token: 0x0400046F RID: 1135
	Private Shared NodeDesc As Translate.Phrase = New Translate.Phrase("ping_node_desc", "An ore node is here")

	' Token: 0x04000470 RID: 1136
	Private Shared NodeMarker As Global.BasePlayer.PingStyle = New Global.BasePlayer.PingStyle(10, 4, Global.BasePlayer.NodeTitle, Global.BasePlayer.NodeDesc, Global.BasePlayer.PingType.Node)

	' Token: 0x04000471 RID: 1137
	Private Shared GunTitle As Translate.Phrase = New Translate.Phrase("ping_gun", "Weapon")

	' Token: 0x04000472 RID: 1138
	Private Shared GunDesc As Translate.Phrase = New Translate.Phrase("ping_weapon_desc", "A dropped weapon is here")

	' Token: 0x04000473 RID: 1139
	Private Shared GunMarker As Global.BasePlayer.PingStyle = New Global.BasePlayer.PingStyle(9, 5, Global.BasePlayer.GunTitle, Global.BasePlayer.GunDesc, Global.BasePlayer.PingType.Gun)

	' Token: 0x04000474 RID: 1140
	Private Shared BuildMarker As Global.BasePlayer.PingStyle = New Global.BasePlayer.PingStyle(12, 5, New Translate.Phrase("", ""), New Translate.Phrase("", ""), Global.BasePlayer.PingType.Build)

	' Token: 0x04000475 RID: 1141
	Private lastTick As TimeSince

	' Token: 0x04000476 RID: 1142
	<TupleElementNames(New String() { "item", "pingType" })>
	Private tutorialDesiredResource As List(Of ValueTuple(Of ItemDefinition, Global.BasePlayer.PingType)) = New List(Of ValueTuple(Of ItemDefinition, Global.BasePlayer.PingType))()

	' Token: 0x04000477 RID: 1143
	<TupleElementNames(New String() { "id", "pingType" })>
	Private pingedEntities As List(Of ValueTuple(Of NetworkableId, Global.BasePlayer.PingType)) = New List(Of ValueTuple(Of NetworkableId, Global.BasePlayer.PingType))()

	' Token: 0x04000478 RID: 1144
	Private lastResourcePingUpdate As TimeSince

	' Token: 0x04000479 RID: 1145
	Private _playerStateDirty As Boolean

	' Token: 0x0400047A RID: 1146
	Private _wipeId As String

	' Token: 0x0400047B RID: 1147
	Private cachedPrivilegeFromOther As Global.BaseEntity

	' Token: 0x0400047C RID: 1148
	Private cachedPrivilegeFromOtherTime As Single

	' Token: 0x0400047D RID: 1149
	<NonSerialized()>
	Public firedProjectiles As Dictionary(Of Integer, Global.BasePlayer.FiredProjectile) = New Dictionary(Of Integer, Global.BasePlayer.FiredProjectile)()

	' Token: 0x0400047E RID: 1150
	<NonSerialized()>
	Public stats As PlayerStatistics

	' Token: 0x0400047F RID: 1151
	<NonSerialized()>
	Public svActiveItemID As ItemId

	' Token: 0x04000480 RID: 1152
	<NonSerialized()>
	Public NextChatTime As Single

	' Token: 0x04000481 RID: 1153
	<NonSerialized()>
	Public nextSuicideTime As Single

	' Token: 0x04000482 RID: 1154
	<NonSerialized()>
	Public nextRespawnTime As Single

	' Token: 0x04000483 RID: 1155
	<NonSerialized()>
	Public respawnId As String

	' Token: 0x04000484 RID: 1156
	Private timeUntilLoadingExpires As RealTimeUntil

	' Token: 0x04000488 RID: 1160
	Public lastPlayerVisibility As Dictionary(Of Global.BaseNetworkable, Single) = New Dictionary(Of Global.BaseNetworkable, Single)()

	' Token: 0x0400048F RID: 1167
	Protected viewAngles As Vector3

	' Token: 0x04000490 RID: 1168
	Private lastSubscriptionTick As Single

	' Token: 0x04000491 RID: 1169
	Private lastPlayerTick As Single

	' Token: 0x04000492 RID: 1170
	Private sleepStartTime As Single = -1F

	' Token: 0x04000493 RID: 1171
	Private fallTickRate As Single = 0.1F

	' Token: 0x04000494 RID: 1172
	Private lastFallTime As Single

	' Token: 0x04000495 RID: 1173
	Private fallVelocity As Single

	' Token: 0x04000496 RID: 1174
	Private cachedNonSuicideHitInfo As HitInfo

	' Token: 0x04000497 RID: 1175
	Public Shared activePlayerList As ListHashSet(Of Global.BasePlayer) = New ListHashSet(Of Global.BasePlayer)(8)

	' Token: 0x04000498 RID: 1176
	Public Shared sleepingPlayerList As ListHashSet(Of Global.BasePlayer) = New ListHashSet(Of Global.BasePlayer)(8)

	' Token: 0x04000499 RID: 1177
	Public Shared bots As ListHashSet(Of Global.BasePlayer) = New ListHashSet(Of Global.BasePlayer)(8)

	' Token: 0x0400049A RID: 1178
	Private cachedCraftLevel As Single

	' Token: 0x0400049B RID: 1179
	Private nextCheckTime As Single

	' Token: 0x0400049C RID: 1180
	Private _cachedWorkbench As Workbench

	' Token: 0x0400049D RID: 1181
	Private cachedPersistantPlayer As PersistantPlayer

	' Token: 0x0400049E RID: 1182
	Private Shared cachedOceanPaths As OceanPaths = Nothing

	' Token: 0x0400049F RID: 1183
	Private Const WILDERNESS As Integer = 1

	' Token: 0x040004A0 RID: 1184
	Private Const MONUMENT As Integer = 2

	' Token: 0x040004A1 RID: 1185
	Private Const BASE As Integer = 4

	' Token: 0x040004A2 RID: 1186
	Private Const FLYING As Integer = 8

	' Token: 0x040004A3 RID: 1187
	Private Const BOATING As Integer = 16

	' Token: 0x040004A4 RID: 1188
	Private Const SWIMMING As Integer = 32

	' Token: 0x040004A5 RID: 1189
	Private Const DRIVING As Integer = 64

	' Token: 0x040004A6 RID: 1190
	<ServerVar()>
	<Help("How many milliseconds to budget for processing life story updates per frame")>
	Public Shared lifeStoryFramebudgetms As Single = 0.25F

	' Token: 0x040004A7 RID: 1191
	<NonSerialized()>
	Public lifeStory As PlayerLifeStory

	' Token: 0x040004A8 RID: 1192
	<NonSerialized()>
	Public previousLifeStory As PlayerLifeStory

	' Token: 0x040004A9 RID: 1193
	Private Const TimeCategoryUpdateFrequency As Single = 7F

	' Token: 0x040004AA RID: 1194
	Private nextTimeCategoryUpdate As Single

	' Token: 0x040004AC RID: 1196
	Private hasSentPresenceState As Boolean

	' Token: 0x040004AD RID: 1197
	Private LifeStoryInWilderness As Boolean

	' Token: 0x040004AE RID: 1198
	Private LifeStoryInMonument As Boolean

	' Token: 0x040004AF RID: 1199
	Private LifeStoryInBase As Boolean

	' Token: 0x040004B0 RID: 1200
	Private LifeStoryFlying As Boolean

	' Token: 0x040004B1 RID: 1201
	Private LifeStoryBoating As Boolean

	' Token: 0x040004B2 RID: 1202
	Private LifeStorySwimming As Boolean

	' Token: 0x040004B3 RID: 1203
	Private LifeStoryDriving As Boolean

	' Token: 0x040004B4 RID: 1204
	Private waitingForLifeStoryUpdate As Boolean

	' Token: 0x040004B5 RID: 1205
	Public Shared lifeStoryQueue As Global.BasePlayer.LifeStoryWorkQueue = New Global.BasePlayer.LifeStoryWorkQueue()

	' Token: 0x040004B6 RID: 1206
	<CanBeNull()>
	Private cachedOverrideDeathInfo As PlayerLifeStory.DeathInfo

	' Token: 0x040004B7 RID: 1207
	Private IsSpectatingTeamInfo As Boolean

	' Token: 0x040004B8 RID: 1208
	Private lastSpectateTeamInfoUpdate As TimeSince

	' Token: 0x040004B9 RID: 1209
	Private SpectateOffset As Integer = 1000000

	' Token: 0x040004BA RID: 1210
	Private spectateFilter As String = ""

	' Token: 0x040004BC RID: 1212
	Private nearbyStashes As List(Of Global.BasePlayer.NearbyStash) = New List(Of Global.BasePlayer.NearbyStash)()

	' Token: 0x040004BD RID: 1213
	Private lastUpdateTime As Single = Single.NegativeInfinity

	' Token: 0x040004BE RID: 1214
	Private cachedThreatLevel As Single

	' Token: 0x040004BF RID: 1215
	<NonSerialized()>
	Public weaponDrawnDuration As Single

	' Token: 0x040004C1 RID: 1217
	<NonSerialized()>
	Private lastTickTime As Single

	' Token: 0x040004C2 RID: 1218
	<NonSerialized()>
	Private lastStallTime As Single

	' Token: 0x040004C3 RID: 1219
	<NonSerialized()>
	Private lastInputTime As Single

	' Token: 0x040004C4 RID: 1220
	<NonSerialized()>
	Private tutorialKickTime As Single

	' Token: 0x040004C5 RID: 1221
	<NonSerialized()>
	Public restraintItemId As ItemId?

	' Token: 0x040004C6 RID: 1222
	Private lastReceivedTick As PlayerTick = New PlayerTick()

	' Token: 0x040004C7 RID: 1223
	Private tickDeltaTime As Single

	' Token: 0x040004C8 RID: 1224
	Private tickNeedsFinalizing As Boolean

	' Token: 0x040004CA RID: 1226
	Private ticksPerSecond As TimeAverageValue = New TimeAverageValue()

	' Token: 0x040004CB RID: 1227
	Private tickInterpolator As TickInterpolator = New TickInterpolator()

	' Token: 0x040004CC RID: 1228
	Public eyeHistory As Deque(Of Vector3) = New Deque(Of Vector3)(8)

	' Token: 0x040004CD RID: 1229
	Public tickHistory As TickHistory = New TickHistory()

	' Token: 0x040004CF RID: 1231
	Private startTutorialCooldown As Single

	' Token: 0x040004D0 RID: 1232
	Private nextUnderwearValidationTime As Single

	' Token: 0x040004D1 RID: 1233
	Private lastValidUnderwearSkin As UInteger

	' Token: 0x040004D2 RID: 1234
	Private woundedDuration As Single

	' Token: 0x040004D3 RID: 1235
	Private lastWoundedStartTime As Single = Single.NegativeInfinity

	' Token: 0x040004D4 RID: 1236
	Private healingWhileCrawling As Single

	' Token: 0x040004D5 RID: 1237
	Private woundedByFallDamage As Boolean

	' Token: 0x040004D6 RID: 1238
	Private Const INCAPACITATED_HEALTH_MIN As Single = 2F

	' Token: 0x040004D7 RID: 1239
	Private Const INCAPACITATED_HEALTH_MAX As Single = 6F

	' Token: 0x040004D8 RID: 1240
	Public Const MaxBotIdRange As Integer = 10000000

	' Token: 0x040004D9 RID: 1241
	<Header("BasePlayer")>
	Public fallDamageEffect As GameObjectRef

	' Token: 0x040004DA RID: 1242
	Public drownEffect As GameObjectRef

	' Token: 0x040004DB RID: 1243
	<Global.InspectorFlags()>
	Public playerFlags As Global.BasePlayer.PlayerFlags

	' Token: 0x040004DC RID: 1244
	Private eyesValue As Global.BasePlayer.HiddenValue(Of PlayerEyes) = Facepunch.Pool.[Get](Of Global.BasePlayer.HiddenValue(Of PlayerEyes))()

	' Token: 0x040004DD RID: 1245
	Private inventoryValue As Global.BasePlayer.HiddenValue(Of Global.PlayerInventory) = Facepunch.Pool.[Get](Of Global.BasePlayer.HiddenValue(Of Global.PlayerInventory))()

	' Token: 0x040004DE RID: 1246
	<NonSerialized()>
	Public blueprints As PlayerBlueprints

	' Token: 0x040004DF RID: 1247
	<NonSerialized()>
	Public metabolism As Global.PlayerMetabolism

	' Token: 0x040004E0 RID: 1248
	<NonSerialized()>
	Public modifiers As Global.PlayerModifiers

	' Token: 0x040004E1 RID: 1249
	Private colliderValue As Global.BasePlayer.HiddenValue(Of CapsuleCollider) = Facepunch.Pool.[Get](Of Global.BasePlayer.HiddenValue(Of CapsuleCollider))()

	' Token: 0x040004E2 RID: 1250
	Public Belt As PlayerBelt

	' Token: 0x040004E3 RID: 1251
	Private playerRigidbody As Rigidbody

	' Token: 0x040004E4 RID: 1252
	<NonSerialized()>
	Public userID As Global.BasePlayer.EncryptedValue(Of ULong) = 0UL

	' Token: 0x040004E5 RID: 1253
	<NonSerialized()>
	Public UserIDString As String

	' Token: 0x040004E6 RID: 1254
	<NonSerialized()>
	Public gamemodeteam As Integer = -1

	' Token: 0x040004E7 RID: 1255
	<NonSerialized()>
	Public reputation As Integer

	' Token: 0x040004E8 RID: 1256
	Protected _displayName As String

	' Token: 0x040004E9 RID: 1257
	Private _lastSetName As String

	' Token: 0x040004EA RID: 1258
	Public Const crouchSpeed As Single = 1.7F

	' Token: 0x040004EB RID: 1259
	Public Const walkSpeed As Single = 2.8F

	' Token: 0x040004EC RID: 1260
	Public Const runSpeed As Single = 5.5F

	' Token: 0x040004ED RID: 1261
	Public Const crawlSpeed As Single = 0.72F

	' Token: 0x040004EE RID: 1262
	Private playerColliderStanding As Global.BasePlayer.CapsuleColliderInfo

	' Token: 0x040004EF RID: 1263
	Private playerColliderDucked As Global.BasePlayer.CapsuleColliderInfo

	' Token: 0x040004F0 RID: 1264
	Private playerColliderCrawling As Global.BasePlayer.CapsuleColliderInfo

	' Token: 0x040004F1 RID: 1265
	Private playerColliderLyingDown As Global.BasePlayer.CapsuleColliderInfo

	' Token: 0x040004F2 RID: 1266
	Private cachedProtection As ProtectionProperties

	' Token: 0x040004F3 RID: 1267
	Private nextColliderRefreshTime As Single = -1F

	' Token: 0x040004F4 RID: 1268
	Public weaponMoveSpeedScale As Single = 1F

	' Token: 0x040004F5 RID: 1269
	Public clothingBlocksAiming As Boolean

	' Token: 0x040004F6 RID: 1270
	Public clothingMoveSpeedReduction As Single

	' Token: 0x040004F7 RID: 1271
	Public clothingWaterSpeedBonus As Single

	' Token: 0x040004F8 RID: 1272
	Public clothingAccuracyBonus As Single

	' Token: 0x040004F9 RID: 1273
	Public equippingBlocked As Boolean

	' Token: 0x040004FA RID: 1274
	Public eggVision As Single

	' Token: 0x040004FB RID: 1275
	Private activeTelephone As PhoneController

	' Token: 0x040004FC RID: 1276
	Public designingAIEntity As Global.BaseEntity

	' Token: 0x02000D77 RID: 3447
	Public Enum CameraMode
		' Token: 0x04004E15 RID: 19989
		FirstPerson
		' Token: 0x04004E16 RID: 19990
		ThirdPerson
		' Token: 0x04004E17 RID: 19991
		Eyes
		' Token: 0x04004E18 RID: 19992
		FirstPersonWithArms
		' Token: 0x04004E19 RID: 19993
		DeathCamClassic
		' Token: 0x04004E1A RID: 19994
		Last = 3
	End Enum

	' Token: 0x02000D78 RID: 3448
	Public Enum NetworkQueue
		' Token: 0x04004E1C RID: 19996
		Update
		' Token: 0x04004E1D RID: 19997
		UpdateDistance
		' Token: 0x04004E1E RID: 19998
		Count
	End Enum

	' Token: 0x02000D79 RID: 3449
	Private Class NetworkQueueList
		' Token: 0x06005C03 RID: 23555 RVA: 0x001FCE61 File Offset: 0x001FB061
		Public Function Contains(ent As Global.BaseNetworkable) As Boolean
			Return Me.queueInternal.Contains(ent)
		End Function

		' Token: 0x06005C04 RID: 23556 RVA: 0x001FCE6F File Offset: 0x001FB06F
		Public Sub Add(ent As Global.BaseNetworkable)
			If Not Me.Contains(ent) Then
				Me.queueInternal.Add(ent)
			End If
			Me.MaxLength = Mathf.Max(Me.MaxLength, Me.queueInternal.Count)
		End Sub

		' Token: 0x06005C05 RID: 23557 RVA: 0x001FCEA4 File Offset: 0x001FB0A4
		Public Sub Add(ent As Global.BaseNetworkable())
			For Each ent2 As Global.BaseNetworkable In ent
				Me.Add(ent2)
			Next
		End Sub

		' Token: 0x170007D1 RID: 2001
		' (get) Token: 0x06005C06 RID: 23558 RVA: 0x001FCECC File Offset: 0x001FB0CC
		Public ReadOnly Property Length As Integer
			Get
				Return Me.queueInternal.Count
			End Get
		End Property

		' Token: 0x06005C07 RID: 23559 RVA: 0x001FCEDC File Offset: 0x001FB0DC
		Public Sub Clear(group As Group)
			Using TimeWarning.[New]("NetworkQueueList.Clear", 0)
				If group IsNot Nothing Then
					If Not group.isGlobal Then
						Dim list As List(Of Global.BaseNetworkable) = Facepunch.Pool.GetList(Of Global.BaseNetworkable)()
						For Each baseNetworkable As Global.BaseNetworkable In Me.queueInternal
							If Not(baseNetworkable Is Nothing) Then
								Dim net As Networkable = baseNetworkable.net
								If If((net IsNot Nothing), net.group, Nothing) IsNot Nothing AndAlso baseNetworkable.net.group IsNot group Then
									Continue For
								End If
							End If
							list.Add(baseNetworkable)
						Next
						For Each item As Global.BaseNetworkable In list
							Me.queueInternal.Remove(item)
						Next
						Facepunch.Pool.FreeList(Of Global.BaseNetworkable)(list)
					End If
				Else
					Dim hashSet As HashSet(Of Global.BaseNetworkable) = Me.queueInternal
					Dim <>9__6_ As Predicate(Of Global.BaseNetworkable) = Global.BasePlayer.NetworkQueueList.<>c.<>9__6_0
					Dim match As Predicate(Of Global.BaseNetworkable) = <>9__6_
					If <>9__6_ Is Nothing Then
						Dim predicate As Predicate(Of Global.BaseNetworkable) = Function(x As Global.BaseNetworkable)
							If Not(x Is Nothing) Then
								Dim net2 As Networkable = x.net
								If If((net2 IsNot Nothing), net2.group, Nothing) IsNot Nothing Then
									Return Not x.net.group.isGlobal
								End If
							End If
							Return True
						End Function
						match = predicate
						Global.BasePlayer.NetworkQueueList.<>c.<>9__6_0 = predicate
					End If
					hashSet.RemoveWhere(match)
				End If
			End Using
		End Sub

		' Token: 0x04004E1F RID: 19999
		Public queueInternal As HashSet(Of Global.BaseNetworkable) = New HashSet(Of Global.BaseNetworkable)()

		' Token: 0x04004E20 RID: 20000
		Public MaxLength As Integer
	End Class

	' Token: 0x02000D7A RID: 3450
	<Flags()>
	Public Enum PlayerFlags
		' Token: 0x04004E22 RID: 20002
		Unused1 = 1
		' Token: 0x04004E23 RID: 20003
		Unused2 = 2
		' Token: 0x04004E24 RID: 20004
		IsAdmin = 4
		' Token: 0x04004E25 RID: 20005
		ReceivingSnapshot = 8
		' Token: 0x04004E26 RID: 20006
		Sleeping = 16
		' Token: 0x04004E27 RID: 20007
		Spectating = 32
		' Token: 0x04004E28 RID: 20008
		Wounded = 64
		' Token: 0x04004E29 RID: 20009
		IsDeveloper = 128
		' Token: 0x04004E2A RID: 20010
		Connected = 256
		' Token: 0x04004E2B RID: 20011
		ThirdPersonViewmode = 1024
		' Token: 0x04004E2C RID: 20012
		EyesViewmode = 2048
		' Token: 0x04004E2D RID: 20013
		ChatMute = 4096
		' Token: 0x04004E2E RID: 20014
		NoSprint = 8192
		' Token: 0x04004E2F RID: 20015
		Aiming = 16384
		' Token: 0x04004E30 RID: 20016
		DisplaySash = 32768
		' Token: 0x04004E31 RID: 20017
		Relaxed = 65536
		' Token: 0x04004E32 RID: 20018
		SafeZone = 131072
		' Token: 0x04004E33 RID: 20019
		ServerFall = 262144
		' Token: 0x04004E34 RID: 20020
		Incapacitated = 524288
		' Token: 0x04004E35 RID: 20021
		Workbench1 = 1048576
		' Token: 0x04004E36 RID: 20022
		Workbench2 = 2097152
		' Token: 0x04004E37 RID: 20023
		Workbench3 = 4194304
		' Token: 0x04004E38 RID: 20024
		VoiceRangeBoost = 8388608
		' Token: 0x04004E39 RID: 20025
		ModifyClan = 16777216
		' Token: 0x04004E3A RID: 20026
		LoadingAfterTransfer = 33554432
		' Token: 0x04004E3B RID: 20027
		NoRespawnZone = 67108864
		' Token: 0x04004E3C RID: 20028
		IsInTutorial = 134217728
		' Token: 0x04004E3D RID: 20029
		IsRestrained = 268435456
		' Token: 0x04004E3E RID: 20030
		CreativeMode = 536870912
	End Enum

	' Token: 0x02000D7B RID: 3451
	Public NotInheritable Class GestureIds
		' Token: 0x04004E3F RID: 20031
		Public Const FlashBlindId As UInteger = 235662700UI
	End Class

	' Token: 0x02000D7C RID: 3452
	Public Enum GestureStartSource
		' Token: 0x04004E41 RID: 20033
		ServerAction
		' Token: 0x04004E42 RID: 20034
		Player
	End Enum

	' Token: 0x02000D7D RID: 3453
	Public Enum MapNoteType
		' Token: 0x04004E44 RID: 20036
		Death
		' Token: 0x04004E45 RID: 20037
		PointOfInterest
	End Enum

	' Token: 0x02000D7E RID: 3454
	Public Enum PingType
		' Token: 0x04004E47 RID: 20039
		Hostile
		' Token: 0x04004E48 RID: 20040
		[GoTo]
		' Token: 0x04004E49 RID: 20041
		Dollar
		' Token: 0x04004E4A RID: 20042
		Loot
		' Token: 0x04004E4B RID: 20043
		Node
		' Token: 0x04004E4C RID: 20044
		Gun
		' Token: 0x04004E4D RID: 20045
		Build
		' Token: 0x04004E4E RID: 20046
		LAST = 6
	End Enum

	' Token: 0x02000D7F RID: 3455
	Public Structure PingStyle
		' Token: 0x06005C09 RID: 23561 RVA: 0x001FD027 File Offset: 0x001FB227
		Public Sub New(icon As Integer, colour As Integer, title As Translate.Phrase, desc As Translate.Phrase, pType As Global.BasePlayer.PingType)
			Me.IconIndex = icon
			Me.ColourIndex = colour
			Me.PingTitle = title
			Me.PingDescription = desc
			Me.Type = pType
		End Sub

		' Token: 0x04004E4F RID: 20047
		Public IconIndex As Integer

		' Token: 0x04004E50 RID: 20048
		Public ColourIndex As Integer

		' Token: 0x04004E51 RID: 20049
		Public PingTitle As Translate.Phrase

		' Token: 0x04004E52 RID: 20050
		Public PingDescription As Translate.Phrase

		' Token: 0x04004E53 RID: 20051
		Public Type As Global.BasePlayer.PingType
	End Structure

	' Token: 0x02000D80 RID: 3456
	Public Structure FiredProjectileUpdate
		' Token: 0x04004E54 RID: 20052
		Public OldPosition As Vector3

		' Token: 0x04004E55 RID: 20053
		Public NewPosition As Vector3

		' Token: 0x04004E56 RID: 20054
		Public OldVelocity As Vector3

		' Token: 0x04004E57 RID: 20055
		Public NewVelocity As Vector3

		' Token: 0x04004E58 RID: 20056
		Public Mismatch As Single

		' Token: 0x04004E59 RID: 20057
		Public PartialTime As Single
	End Structure

	' Token: 0x02000D81 RID: 3457
	Public Class FiredProjectile
		Implements Facepunch.Pool.IPooled

		' Token: 0x06005C0A RID: 23562 RVA: 0x001FD050 File Offset: 0x001FB250
		Public Sub EnterPool() Implements Facepunch.Pool.IPooled.EnterPool
			Me.itemDef = Nothing
			Me.itemMod = Nothing
			Me.projectilePrefab = Nothing
			Me.firedTime = 0F
			Me.travelTime = 0F
			Me.partialTime = 0F
			Me.weaponSource = Nothing
			Me.weaponPrefab = Nothing
			Me.projectileModifier = Nothing
			Me.pickupItem = Nothing
			Me.integrity = 0F
			Me.trajectoryMismatch = 0F
			Me.position = Nothing
			Me.velocity = Nothing
			Me.initialPosition = Nothing
			Me.initialVelocity = Nothing
			Me.inheritedVelocity = Nothing
			Me.protection = 0
			Me.ricochets = 0
			Me.hits = 0
			Me.lastEntityHit = Nothing
			Me.desyncLifeTime = 0F
			Me.id = 0
			Me.attacker = Nothing
			Me.updates.Clear()
			Me.simulatedPositions.Clear()
		End Sub

		' Token: 0x06005C0B RID: 23563 RVA: 0x001FD151 File Offset: 0x001FB351
		Public Sub LeavePool() Implements Facepunch.Pool.IPooled.LeavePool
		End Sub

		' Token: 0x04004E5A RID: 20058
		Public itemDef As ItemDefinition

		' Token: 0x04004E5B RID: 20059
		Public itemMod As ItemModProjectile

		' Token: 0x04004E5C RID: 20060
		Public projectilePrefab As Projectile

		' Token: 0x04004E5D RID: 20061
		Public firedTime As Single

		' Token: 0x04004E5E RID: 20062
		Public travelTime As Single

		' Token: 0x04004E5F RID: 20063
		Public partialTime As Single

		' Token: 0x04004E60 RID: 20064
		Public weaponSource As AttackEntity

		' Token: 0x04004E61 RID: 20065
		Public weaponPrefab As AttackEntity

		' Token: 0x04004E62 RID: 20066
		Public projectileModifier As Projectile.Modifier

		' Token: 0x04004E63 RID: 20067
		Public pickupItem As Global.Item

		' Token: 0x04004E64 RID: 20068
		Public integrity As Single

		' Token: 0x04004E65 RID: 20069
		Public trajectoryMismatch As Single

		' Token: 0x04004E66 RID: 20070
		Public position As Vector3

		' Token: 0x04004E67 RID: 20071
		Public initialPositionOffset As Vector3

		' Token: 0x04004E68 RID: 20072
		Public positionOffset As Vector3

		' Token: 0x04004E69 RID: 20073
		Public velocity As Vector3

		' Token: 0x04004E6A RID: 20074
		Public initialPosition As Vector3

		' Token: 0x04004E6B RID: 20075
		Public initialVelocity As Vector3

		' Token: 0x04004E6C RID: 20076
		Public inheritedVelocity As Vector3

		' Token: 0x04004E6D RID: 20077
		Public protection As Integer

		' Token: 0x04004E6E RID: 20078
		Public ricochets As Integer

		' Token: 0x04004E6F RID: 20079
		Public hits As Integer

		' Token: 0x04004E70 RID: 20080
		Public lastEntityHit As Global.BaseEntity

		' Token: 0x04004E71 RID: 20081
		Public desyncLifeTime As Single

		' Token: 0x04004E72 RID: 20082
		Public id As Integer

		' Token: 0x04004E73 RID: 20083
		Public attacker As Global.BasePlayer

		' Token: 0x04004E74 RID: 20084
		Public updates As List(Of Global.BasePlayer.FiredProjectileUpdate) = New List(Of Global.BasePlayer.FiredProjectileUpdate)()

		' Token: 0x04004E75 RID: 20085
		Public simulatedPositions As List(Of Vector3) = New List(Of Vector3)()
	End Class

	' Token: 0x02000D82 RID: 3458
	Public Class SpawnPoint
		' Token: 0x04004E76 RID: 20086
		Public pos As Vector3

		' Token: 0x04004E77 RID: 20087
		Public rot As Quaternion
	End Class

	' Token: 0x02000D83 RID: 3459
	Public Enum TimeCategory
		' Token: 0x04004E79 RID: 20089
		Wilderness = 1
		' Token: 0x04004E7A RID: 20090
		Monument
		' Token: 0x04004E7B RID: 20091
		Base = 4
		' Token: 0x04004E7C RID: 20092
		Flying = 8
		' Token: 0x04004E7D RID: 20093
		Boating = 16
		' Token: 0x04004E7E RID: 20094
		Swimming = 32
		' Token: 0x04004E7F RID: 20095
		Driving = 64
	End Enum

	' Token: 0x02000D84 RID: 3460
	Public Class LifeStoryWorkQueue
		Inherits ObjectWorkQueue(Of Global.BasePlayer)

		' Token: 0x06005C0E RID: 23566 RVA: 0x001FD179 File Offset: 0x001FB379
		Protected Overrides Sub RunJob(entity As Global.BasePlayer)
			entity.UpdateTimeCategory()
		End Sub

		' Token: 0x06005C0F RID: 23567 RVA: 0x001FD181 File Offset: 0x001FB381
		Protected Overrides Function ShouldAdd(entity As Global.BasePlayer) As Boolean
			Return MyBase.ShouldAdd(entity) AndAlso entity.IsValid()
		End Function
	End Class

	' Token: 0x02000D85 RID: 3461
	Private Class NearbyStash
		' Token: 0x06005C11 RID: 23569 RVA: 0x001FD19C File Offset: 0x001FB39C
		Public Sub New(stash As StashContainer)
			Me.Entity = stash
			Me.LookingAtTime = 0F
		End Sub

		' Token: 0x04004E80 RID: 20096
		Public Entity As StashContainer

		' Token: 0x04004E81 RID: 20097
		Public LookingAtTime As Single
	End Class

	' Token: 0x02000D86 RID: 3462
	Public Enum TutorialItemAllowance
		' Token: 0x04004E83 RID: 20099
		AlwaysAllowed = -1
		' Token: 0x04004E84 RID: 20100
		None
		' Token: 0x04004E85 RID: 20101
		Level1_HatchetPickaxe = 10
		' Token: 0x04004E86 RID: 20102
		Level2_Planner = 20
		' Token: 0x04004E87 RID: 20103
		Level3_Bag_TC_Door = 30
		' Token: 0x04004E88 RID: 20104
		Level3_Hammer = 35
		' Token: 0x04004E89 RID: 20105
		Level4_Spear_Fire = 40
		' Token: 0x04004E8A RID: 20106
		Level5_PrepareForCombat = 50
		' Token: 0x04004E8B RID: 20107
		Level6_Furnace = 60
		' Token: 0x04004E8C RID: 20108
		Level7_WorkBench = 70
		' Token: 0x04004E8D RID: 20109
		Level8_Kayak = 80
	End Enum

	' Token: 0x02000D87 RID: 3463
	<Serializable()>
	Public Structure CapsuleColliderInfo
		' Token: 0x06005C12 RID: 23570 RVA: 0x001FD1B6 File Offset: 0x001FB3B6
		Public Sub New(height As Single, radius As Single, center As Vector3)
			Me.height = height
			Me.radius = radius
			Me.center = center
		End Sub

		' Token: 0x04004E8E RID: 20110
		Public height As Single

		' Token: 0x04004E8F RID: 20111
		Public radius As Single

		' Token: 0x04004E90 RID: 20112
		Public center As Vector3
	End Structure

	' Token: 0x02000D88 RID: 3464
	Public NotInheritable Class HiddenValue(Of T As Class)
		Implements Facepunch.Pool.IPooled, IDisposable

		' Token: 0x06005C13 RID: 23571 RVA: 0x001FD1D0 File Offset: 0x001FB3D0
		Public Sub New()
			Me.New(Nothing)
		End Sub

		' Token: 0x06005C14 RID: 23572 RVA: 0x001FD1EC File Offset: 0x001FB3EC
		Public Sub New(value As T)
			Me._handle.[Set](Nothing)
			Me._accessCount = 0
			If value IsNot Nothing Then
				Me.[Set](value)
			End If
		End Sub

		' Token: 0x06005C15 RID: 23573 RVA: 0x001FD22C File Offset: 0x001FB42C
		<MethodImpl(MethodImplOptions.AggressiveInlining)>
		Public Function [Get]() As T
			Dim gchandle As GCHandle = Me._handle.[Get]()
			If Not gchandle.IsAllocated Then
				Return Nothing
			End If
			Dim t As T = CType(CObj(gchandle.Target), T)
			Me._accessCount += 1
			If Me._accessCount >= 1000 Then
				Me._accessCount = 0
				Dim value As GCHandle = GCHandle.Alloc(t, GCHandleType.Normal)
				gchandle.Free()
				Me._handle.[Set](value)
			End If
			Return t
		End Function

		' Token: 0x06005C16 RID: 23574 RVA: 0x001FD2A8 File Offset: 0x001FB4A8
		<MethodImpl(MethodImplOptions.AggressiveInlining)>
		Public Function [Set](value As T) As Global.BasePlayer.HiddenValue(Of T)
			Dim gchandle As GCHandle = Me._handle.[Get]()
			If value Is Nothing Then
				If gchandle.IsAllocated Then
					gchandle.Free()
				End If
				Me._handle.[Set](Nothing)
				Return Me
			End If
			Dim value2 As GCHandle = GCHandle.Alloc(value, GCHandleType.Normal)
			If gchandle.IsAllocated Then
				gchandle.Free()
			End If
			Me._handle.[Set](value2)
			Return Me
		End Function

		' Token: 0x06005C17 RID: 23575 RVA: 0x001FD31C File Offset: 0x001FB51C
		Sub EnterPool() Implements Facepunch.Pool.IPooled.EnterPool
			Me.[Set](Nothing)
		End Sub

		' Token: 0x06005C18 RID: 23576 RVA: 0x001FD339 File Offset: 0x001FB539
		Sub LeavePool() Implements Facepunch.Pool.IPooled.LeavePool
		End Sub

		' Token: 0x06005C19 RID: 23577 RVA: 0x001FD33C File Offset: 0x001FB53C
		Public Sub Dispose() Implements System.IDisposable.Dispose
			Me.[Set](Nothing)
			Dim hiddenValue As Global.BasePlayer.HiddenValue(Of T) = Me
			Facepunch.Pool.Free(Of Global.BasePlayer.HiddenValue(Of T))(hiddenValue)
		End Sub

		' Token: 0x06005C1A RID: 23578 RVA: 0x001FD362 File Offset: 0x001FB562
		<MethodImpl(MethodImplOptions.AggressiveInlining)>
		Public Shared Widening Operator CType(hidden As Global.BasePlayer.HiddenValue(Of T)) As T
			Return hidden.[Get]()
		End Operator

		' Token: 0x04004E91 RID: 20113
		Private _handle As Global.BasePlayer.HiddenValue_Internal_EncryptedValue(Of GCHandle)

		' Token: 0x04004E92 RID: 20114
		Private _accessCount As Integer
	End Class

	' Token: 0x02000D89 RID: 3465
	Public Structure HiddenValue_Internal_EncryptedValue(Of TInner As{Structure, ValueType})
		' Token: 0x06005C1B RID: 23579 RVA: 0x001FD36A File Offset: 0x001FB56A
		<MethodImpl(MethodImplOptions.AggressiveInlining)>
		Public Function [Get]() As TInner
			Return Me._value
		End Function

		' Token: 0x06005C1C RID: 23580 RVA: 0x001FD372 File Offset: 0x001FB572
		<MethodImpl(MethodImplOptions.AggressiveInlining)>
		Public Sub [Set](value As TInner)
			Me._value = value
		End Sub

		' Token: 0x06005C1D RID: 23581 RVA: 0x001FD37C File Offset: 0x001FB57C
		Public Overrides Function ToString() As String
			Dim tinner As TInner = Me.[Get]()
			Return tinner.ToString()
		End Function

		' Token: 0x06005C1E RID: 23582 RVA: 0x001FD3A0 File Offset: 0x001FB5A0
		<MethodImpl(MethodImplOptions.AggressiveInlining)>
		Public Shared Widening Operator CType(value As TInner) As Global.BasePlayer.HiddenValue_Internal_EncryptedValue(Of TInner)
			Dim result As Global.BasePlayer.HiddenValue_Internal_EncryptedValue(Of TInner) = Nothing
			result.[Set](value)
			Return result
		End Operator

		' Token: 0x06005C1F RID: 23583 RVA: 0x001FD3BE File Offset: 0x001FB5BE
		<MethodImpl(MethodImplOptions.AggressiveInlining)>
		Public Shared Widening Operator CType(encrypted As Global.BasePlayer.HiddenValue_Internal_EncryptedValue(Of TInner)) As TInner
			Return encrypted.[Get]()
		End Operator

		' Token: 0x04004E93 RID: 20115
		Private _value As TInner
	End Structure

	' Token: 0x02000D8A RID: 3466
	Public Structure EncryptedValue(Of TInner As{Structure, ValueType})
		' Token: 0x06005C20 RID: 23584 RVA: 0x001FD3C7 File Offset: 0x001FB5C7
		<MethodImpl(MethodImplOptions.AggressiveInlining)>
		Public Function [Get]() As TInner
			Return Me._value
		End Function

		' Token: 0x06005C21 RID: 23585 RVA: 0x001FD3CF File Offset: 0x001FB5CF
		<MethodImpl(MethodImplOptions.AggressiveInlining)>
		Public Sub [Set](value As TInner)
			Me._value = value
		End Sub

		' Token: 0x06005C22 RID: 23586 RVA: 0x001FD3D8 File Offset: 0x001FB5D8
		Public Overrides Function ToString() As String
			Dim tinner As TInner = Me.[Get]()
			Return tinner.ToString()
		End Function

		' Token: 0x06005C23 RID: 23587 RVA: 0x001FD3FC File Offset: 0x001FB5FC
		<MethodImpl(MethodImplOptions.AggressiveInlining)>
		Public Shared Widening Operator CType(value As TInner) As Global.BasePlayer.EncryptedValue(Of TInner)
			Dim result As Global.BasePlayer.EncryptedValue(Of TInner) = Nothing
			result.[Set](value)
			Return result
		End Operator

		' Token: 0x06005C24 RID: 23588 RVA: 0x001FD41A File Offset: 0x001FB61A
		<MethodImpl(MethodImplOptions.AggressiveInlining)>
		Public Shared Widening Operator CType(encrypted As Global.BasePlayer.EncryptedValue(Of TInner)) As TInner
			Return encrypted.[Get]()
		End Operator

		' Token: 0x04004E94 RID: 20116
		Private _value As TInner
	End Structure
End Class
