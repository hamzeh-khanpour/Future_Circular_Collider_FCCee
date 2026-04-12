#include <TCanvas.h>
#include <TGraph.h>
#include <TArrow.h>

void FCC_tqz() {
    // Define the data points
    const Int_t n = 6;
    Double_t x[n] = {3.25e-5,8.19e-6, 2.4e-4, 8.18e-6, 5.60e-5, 2.26e-5};
    Double_t y[n] = { 6, 5, 4, 3, 2, 1};

    // Define the error values
    Double_t low1dg[n] = {1e-1, 1e-1, 1e-1, 1e-1, 1e-1, 1e-1};
    Double_t up1dg[n] = {0.0, 0.0, 0.0, 0.0, 0.0, 0.0};

    // Define the row names
    TString rowNames[n] = {
        "13TeV 139 fb^{-1} ATLAS",
        "8TeV 19.8 fb^{-1} CMS",
        //"240GeV 3 ab^{-1} FCC-ee",
        //"350GeV 3 ab^{-1} FCC-ee",
        "100TeV 10 ab^{-1} FCC-hh",
        "27TeV 15 ab^{-1} FCC-hh",
	"LDC Combination",
        "HDC Combination"
    };

    // Create a canvas to draw the graph
    TCanvas* canvas = new TCanvas("canvas", "Error Bars with Arrows", 800, 600);
    canvas->SetMargin(0.2, 0.02, 0.1, 0.1); // Adjust the margins to accommodate row names

    // Create a TGraph to plot the data points
    TGraph* gr1 = new TGraph(n, x, y);
    gr1->SetMarkerStyle(20);  // Set marker style as desired
    gr1->GetXaxis()->SetLimits(1e-8, 1e-1);
    gr1->Draw("AP");
    gr1->SetTitle("Br(t#rightarrow Zq)");
    // Draw the graph with markers and axes

    // Draw error bars with arrows and row names
    for (Int_t i = 0; i < n; i++) {
        Double_t posX = x[i];
        Double_t posY = y[i];
        Double_t errXLow = low1dg[i];
        Double_t errXUp = up1dg[i];
        Double_t errYLow = 0;
        Double_t errYUp = up1dg[i];

        TArrow* arrow = new TArrow(posX - errXLow, posY, posX + errXUp, posY, 0.02, "<|");
        arrow->SetLineWidth(1);
        arrow->SetLineColor(kBlack);
        arrow->Draw();

        TLatex* text = new TLatex(posX, posY, rowNames[i]);
        text->SetTextAlign(21);
        text->SetTextSize(0.02);
        text->SetTextAngle(0);
        text->Draw();
    }

    // Update the canvas
    canvas->SetLogx();
    canvas->Update();

    canvas->SaveAs("/home/user1/Dropbox/FCNC_FCCee_Full_Analysis/FCC_Physics_Workshop_Krakow_2023/PresentationKrakow_2023/tqz_compare2.pdf");
    canvas->SaveAs("/home/user1/Dropbox/FCNC_FCCee_Full_Analysis/FCC_Physics_Workshop_Krakow_2023/PresentationKrakow_2023/tqz_compare2.png");
}
