package clientname.ui;

import java.io.IOException;
import java.text.Collator;

import org.lwjgl.util.Color;

import clientname.clientname;
import net.minecraft.client.gui.FontRenderer;
import net.minecraft.client.gui.Gui;
import net.minecraft.client.gui.GuiButton;
import net.minecraft.client.gui.GuiMultiplayer;
import net.minecraft.client.gui.GuiOptions;
import net.minecraft.client.gui.GuiScreen;
import net.minecraft.client.gui.GuiSelectWorld;
import net.minecraft.client.renderer.GlStateManager;
import net.minecraft.util.ResourceLocation;

public class HylexmcMainMenu extends GuiScreen{
	
	@Override
	public void drawScreen(int mouseX, int mouseY, float partialTicks) {
		mc.getTextureManager().bindTexture(new ResourceLocation("CLIENTNAME/picname.jpg"));
		Gui.drawModalRectWithCustomSizedTexture(-21 + (mouseX / 90), ((mouseY) * -1 / 90), 0, 0, width + 20, height + 20, width + 21, height + 20);
		
		GlStateManager.pushMatrix();
		GlStateManager.translate(width/2f, height/2f, 0);
		GlStateManager.scale(3, 3, 1);
		GlStateManager.translate(-(width/2f), -(height/2f), 0);
		this.drawCenteredString(mc.fontRendererObj, Hylexmc.INSTANCE.NAME, width/2.5f, height/2.5f - mc.fontRendererObj.FONT_HEIGHT/2f, -1);
		GlStateManager.popMatrix();
		mc.fontRendererObj.drawStringWithShadow(Hylexmc.INSTANCE.VERSION, width/2f +60, height/2f - mc.fontRendererObj.FONT_HEIGHT * 2f, new Color(0,0,255, 255).getRed());
		
		
		super.drawScreen(mouseX, mouseY, partialTicks);
	}
	

	@Override
	public void initGui() {
		this.buttonList.add(new GuiButton(1, 5, height / 2 - 40,"Singleplayer"));
		this.buttonList.add(new GuiButton(2, 5, height / 2 - 15,"Multiplayer"));
		this.buttonList.add(new GuiButton(3, 5, height / 2 + 10 ,"Settings"));
		this.buttonList.add(new GuiButton(4, 5, height / 2 + 35,"Rage quit||1111"));
		super.initGui();
	}
	
	@Override
	protected void actionPerformed(GuiButton button) throws IOException {
		if(button.id == 1) {
			mc.displayGuiScreen(new GuiSelectWorld(this));
		}
		if(button.id == 2) {
			mc.displayGuiScreen(new GuiMultiplayer(this));
		}
		if(button.id == 3) {
			mc.displayGuiScreen(new GuiOptions(this, mc.gameSettings));
		}
		if(button.id == 4) {
			mc.shutdown();
		}
		
		super.actionPerformed(button);
	}

}
